#iOS多线程之NSOperation/NSOperationQueue
NSOperation, NSOperationQueue是苹果基于 GCD 的更高一层的封装, 是完全面向对象的, 代码的可读性也更强.

* 使用 NSOperation 和 NSOperationQueue可以完成以下基本的操作:

	* 可添加完成的代码块，在操作完成后执行。
	* 添加操作之间的依赖关系，方便的控制执行顺序.
	* 设定操作执行的优先级。
	* 可以很方便的取消一个操作的执行
	* 使用 KVO 观察对操作执行状态的更改：isExecuteing、isFinished、isCancelled。
* 在 NSOperationQueue 中是通过<mark>最大并发操作数(maxConcurrentOperationCount)</mark>来控制串行和并发的, 

	* maxConcurrentOperationCount = -1; (默认状态, 并行队列, 根据实际情况确定并发数, 会开启新线程)
	* maxConcurrentOperationCount = 1; (串行队列, 会串行执行, 但不在主线程中执行, 任会开启新线程)
	* maxConcurrentOperationCount > 1; (并行队列, 并发数根据设置的值情定, 当设置的值过大时, 系统会指定对值进行调整, 线程开得越多, 消耗的内存越多, 影响性能, 这是系统不允许的)

###NSOperation 和 NSOperationQueue 的使用
