# socket.emitOn
socket.io client promise emit on

## example

```javascript
  import io from 'socket.io-client'

  const socket = io(`//127.0.0.1:3000/`)

  /**
   * socket触发事件 并监听回调 返回promise
   * @param  {[type]} event [description]
   * @param  {[type]} param [description]
   * @return {[type]}       [description]
   */
  socket.emitOn = (event, param) => {
    let promise = new Promise((resolve, reject) => {
      // 重新绑定事件
      socket.once(event, data => {
        resolve(data)
      })

      // 触发事件
      socket.emit(event, param)
    })

    return promise
  }

  export default socket

```
