# glDebug
Setting up apitrace with MultiMC: [Tutorial](https://gist.github.com/Sturmlilie/69d6c4d2dce9d648cd706093c95ba195)
## As a stand-alone mod
glDebug contains common annotation for OpenGL-intensive methods in Minecraft 1.15.2 which are automatically inserted via mixin-hooks, including:  
`DiffuseLighting`, `DrawableHelper`, `GameRenderer`, `ItemRenderer`, `ModelLoader`, `Screen`, `SpriteAtlasTexture`, `TextureManager`, `WorldRenderer`
Also contains a special annotater for `RenderLayer` instances, and an optional annotater which hooks into Minecrafts own Profiler (off by default).

**Without glDebug:**  
![without_gldebug](https://imgur.com/0ctOB9K.png)

**With glDebug:**  
![with_gldebug](https://imgur.com/4pxNePM.png)
## As a library
Insert your own structuring annotations. Sample:
```java
/* imports ... */
import net.ancurio.gldebug.trace.Annotater;
/* constructors ... */
Annotater tater = Annotater.chooseImpl("tis3d");
tater.appendPrefix("serialport");
/* render methods ... */
tater.push("SerialPortModule.render");
ignoreLighting();
tater.pop();
```
Result:
![result](https://imgur.com/v3LMhCC.png)

## Todo
* Minecraft 1.16
* Sodium / fabric rendering API support (as soon as those are stable)
* Configuration file
* Auto-generated mixin hooks

## License
LGPLv3