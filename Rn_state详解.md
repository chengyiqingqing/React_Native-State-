# React Native 的state使用详解

[TOC]

### 1.什么是state?

​	我们使用两种数据来控制一个组件：props和state。props是在父组件中指定，而且一经指定，在被指定的组件的生命周期中则不再改变。 对于需要改变的数据，我们需要使用`state`。

​	一般来说，你需要在constructor中初始化    `state` （译注：这是ES6的写法，早期的很多ES5的例子使用的是getInitialState方法来初始化state，这一做法会逐渐被淘汰）， 然后在需要修改时调用 `setState` 方法。

### 2.如何使用state?

​	两种方式使用state:猜想这一种可能是全局的属于类的。而第二种属于对象的.(回头验证一下)

```react native
    //方式1：猜想这一种可能是全局的属于类的。而第二种属于对象的。
    state={
        size:80,
    }

    //方式2：
    constructor(props){
        super(props);
        /*this.state={
            size:80,
        }*/
    }

	render(){
        return(
            <Text
                style={{fontSize:20 , backgroundColor:'red' }}
                onPress={()=>{
                    this.setState({
                        size:this.state.size+20
                    })
                }}
                >
                {this.state.size}
            </Text>
        )
    }
```



### 3.state也可以吹气球？

​	将state的值进行利用达到更新的效果

```
render(){
        return(
            <View>
                <Text
                    style={{fontSize:20 , backgroundColor:'red' }}
                    onPress={()=>{
                        this.setState({
                            size:this.state.size+20
                        })
                    }}
                >
                    {this.state.size}
                </Text>
                <Image
                    style={{width:this.state.size,height:this.state.size}}
                    source={require('./bom.png')}
                />
                <Text
                    style={{fontSize:20 , backgroundColor:'red' }}
                    onPress={()=>{
                        this.setState({
                            size:this.state.size-20
                        })
                    }}
                >
                    {this.state.size}
                </Text>
            </View>
        )
    }
```





