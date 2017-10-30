* flask信号：Flask的信号功能是基于Python消息分发组件Blinker之上的。Flask 自身有许多信号，其他扩展可能还会带来更多信号。
1. 信号(Signal)就是两个独立的模块用来传递消息的方式，它有一个消息的发送者Sender，还有一个消息的订阅者Subscriber。
2. flask内置信号：
* template_rendered = _signals.signal('template-rendered’)：模板渲染成功的时候发送，这个信号与模板实例template上下文的字典一起调用。
* before_render_template = _signals.signal('before-render-template')
* request_started = _signals.signal('request-started’)：建立请求上下文后，在请求处理开始前发送，订阅者可以用request之类的标准代理访问请求。
* request_finished = _signals.signal('request-finished’)：在响应发送给客户端之前发送，可以传递reponse。
* request_tearing_down = _signals.signal('request-tearing-down’)：在请求销毁时发送，它总是被调用，即使发生异常。
* got_request_exception = _signals.signal('got-request-exception’)：在请求处理中抛出异常时发送，异常本身会通过execption传递到订阅函数。
* appcontext_tearing_down = _signals.signal('appcontext-tearing-down’)：在应用上下文销毁时发送，它总是被调用，即使发生异常。
* appcontext_pushed = _signals.signal('appcontext-pushed')
* appcontext_popped = _signals.signal('appcontext-popped')
* message_flashed = _signals.signal('message-flashed’)
3. 发送信号：
* 发送信号消息的方法是”send()”，它必须包含一个参数指向信号的发送者。
* ”send()”方法可以有多个参数，从第二个参数开始是可选的，如果你要提供，就必须是key=value形式。而这个key就可以在订阅回调函数中接收。
4. 订阅信号：
* 信号的connect（）方法可以订阅该信号，该方法的第一个参数是当信号发出时所调用的函数，第二个参数是可选参数（定义一个发送者）。
* 信号的connect_via（）方法可以订阅该信号，可以使用该装饰器函数装饰接收信号的函数，第一个参数是信号发送者。
* 使用disconnect（）方法退订信号。
5. 所有核心flask信号的发送者是应用本身。因此，当订阅信号时请指定发送者，除非你真的想接收所有应用的信号。
6. Flask-SQLAlchemy内置信号：（如果配置中 SQLALCHEMY_TRACK_MODIFICATIONS 启用的话，这些更新变化才能被追踪。）
* models_committed信号：这个信号在修改的模型提交到数据库时发出。发送者是发送修改的应用，模型和操作描述符以 (model, operation) 形式作为元组，这样的元组列表传递给接受者的 changes 参数。该模型是发送到数据库的模型实例，当一个模型已经插入，操作是 'insert' ，而已删除是 'delete' ，如果更新了任何列，会是 'update' 。
* before_models_committed信号：工作机制和 models_committed 完全一样，但是在提交之前发送。
* 使用上面这两个信号，需要pip install https://github.com/mitsuhiko/flask-sqlalchemy/tarball/master
7. 如果信号接收函数内报错的话，信号触发函数不会有影响。
8. 信号在接收时，完全支持请求上下文。上下文本地的变量在 request_started 和 request_finished 一贯可用，所以你可以信任 flask.g 和其他需要的东西。
9. 如果将信号处理部分单独写成一个模块，则需要在config文件中或者run.py文件中import 导入该模块，进行注册，这样才能生效。
