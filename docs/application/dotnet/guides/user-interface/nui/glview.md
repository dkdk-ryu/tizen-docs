# GLView

NUI `GLView` is a component for rendering content with OpenGLES. It allows you to render 3D objects with OpenGLES.
GLView creates a context, a surface, and a render thread. The render thread invokes user's callbacks (GLInitialize, GLRenderFrame, GLTerminate, Resize)

## Create an GLView

To create an GLView, follow these steps:

1.  Put ColorFormat in the GLView constructor.

    ```csharp
    glView = new GLView(GLView.ColorFormat.RGBA8888);
    ```

2. Set the rendering mode. There are Continuous and OnDemand modes.When you set OnDemand, You have to call RenderOnce() method to invoke the GLRenderFrame callback in the render thread.

    ```csharp
    glView.RenderingMode = Tizen.NUI.GLRenderingMode.Continuous;
    ```

3. Set graphis configuration. you have to set surface configuration and GLES version.
    ```csharp
    glView.SetGraphicsConfig(true, true, 0, Tizen.NUI.GLESVersion.Version20);
    ```

4. Register GLInit, GLRender, GLTerminate callbacks.
    ```csharp
    glView.RegisterGLCallbacks(this.InitializeGL, this.RenderFrameGL, this.Terminate.GL);
    ```

5. Set resize callback. You can get the resized size of the GLView on the render thread.
    ```csharp
    glView.SetResizeCallback(this.ResizeCallback);
    ```

## GLView Callbacks

```csharp
public delegate void GLInitializeDelegate();
public delegate int GLRenderFrameDelegate();
public delegate void GLTerminateDelegate();
public delegate void ViewResizeDelegate(int w, int h);
```


## ImageView properties
The following table defines the GLView class control properties:

Table: ImageView control properties

| Property             | Type        | Description                              |
|--------------------|-----------|----------------------------------------|
| `RenderingMode`        | `GLRenderingMode`    | The rendering mode of GLView        |

Full Source Code.




+ GLView 생성
+ RenderingMode는 GLView안에서가 아니라 Tizen.NUI밑에 있는 enum 타입이고,
Continuous와 OnDemand 가 있음.
+ RegisterGLCallback에는 콜백들을 등록해야하는데 타입들은 3가지가 있음.
+ GLView.GLInitializeDelegate:
public delegate void GLInitializeDelegate()
+ GLView.GLRenderFrameDelegate:
public delegate int GLRenderFrameDelegate()
+ GLView.GLTerminateDelegate:
public delegate void GLTerminateDelegate()

