# PYML 是什么?

PYML 是 Python 版的 QML, 可在声明式 UI 中引用 Python 的模块.

PYML 受 enaml 启发而诞生, 与 enaml 有诸多相似之处.

PYML 写出来的代码看起来长这样:

```pyml
import pyml.qtquick
import pyml.qtquick.controls
import pyml.qtquick.window


comp MyWindow(Window): @win
    visible: True
    color: '#cccccc'
    width: 600
    height: 800
    padding: 10

    Item: @container
        attr active: False
        margins: 20
        size: 'fill'

        Rectangle:
            width: 100
            height: 100
            color: '#ffffff'
            radius: 8
            anim:
                NumberAnimation:
                    when: container.active
                    props:
                        width: parent.width
                        height: parent.height
                    duration: 1000
            Text:
                pos: 'center'
                text: 'Hello World'
            MouseArea:
                size: 'fill'
                on_clicked:
                    container.active = !container.active


if __name__ == '__main__':
    from pyml.core import Application
    with Application() as app:
        win = MyWindow()
        win.show()
        app.start()

```

![](./gallery/pyml-intro.gif)
