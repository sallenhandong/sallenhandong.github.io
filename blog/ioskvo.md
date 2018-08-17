
### IOS KVO原理解析与应用
####一、KVO概述
KVO，即：```Key-Value Observing```，是Objective-C对观察者模式的实现，每次当被观察对象的某个属性值发生改变时，注册的观察者便能获得通知，这种模式有利于两个类间的解耦合，尤其是对于业务逻辑与视图控制 这两个功能的解耦合。
####二、KVO有哪些应用？
- NSOperation
- NSOperationQueue
- RAC
#### 三、KVO的使用和实现？
#####1、使用KVO
1.注册观察者，指定被观察对象的属性： 

	[_people addObserver:self forKeyPath:@"name" options:NSKeyValueObservingOptionOld | NSKeyValueObservingOptionNew context:nil];
2.在观察者中实现以下回调方法：
```
- (void)observeValueForKeyPath:(NSString *)keyPath  
                      ofObject:(id)object  
                        change:(NSDictionary *)change  
                       context:(voidvoid *)context  
   
{  
        NSString *name = [object valueForKey:@"name"]; 
        NSLog(@"new name is: %@", name);  
}  
```
只要People对象中的name属性发生变化，系统会自动调用该方法。

3.最后不要忘了在dealloc中移除观察者
```
[_people removeObserver:self forKeyPath:@"age"]; 
```
##### 2、KVO的实现
KVO 在apple文档的说明

```
Automatic key-value observing is implemented using a technique called 
isa-swizzling… When an observer is registered for an attribute of an object the 
isa pointer of the observed object is modified, pointing to an intermediate class 
rather than at the true class …
```
利用运行时，生成一个对象的子类，并生成子类对象，并替换原来对象的isa指针，且重写了set方法。
####四、KVO的缺陷
KVO很强大，但他的缺点也很明显  
</br>
1.只能重写 `-observeValueForKeyPath:ofObject:change:contex `这个方法 来获得通知,不能使用自定义的`selector`， 想要传一个`block `更是不可能 ，而且还要处理父类的情况 父类同样观察一个同样的属性的情况 ，但是有时候并不知道父类 是不是对这个消息有兴趣。 
</br>
2.父类和子类同时存在KVO时，很容易出现对同一个`keyPath`进行两次`removeObserver`操作，从而导致程序`crash`。要避免这个问题，就需要区分出`KVO`是`self`注册的，还是`superClass`注册的，我们可以在 `-addObserver:forKeyPath:options:context:`和`-removeObserver:forKeyPath:context`这两个方法中传入不同的`context`进行区分。



#####持续更新
