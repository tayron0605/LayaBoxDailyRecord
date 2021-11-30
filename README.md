# LayaBoxDailyRecord

# 20200925
1.Unity import FBX from 3DMax , Material ball must only one, or CustomShader maybe not work.
2.TypeScript: "arr.splice(0,1)" delete the first value in Array;"arr.splice(0)" clear the Array.

# 20200924
1.Unity Particle Color Params warning(If use gradientColor):
  a.GradientDataColor warning:alpha data length is large than 4, will ignore the middle data.
  b.GradientDataColor warning:rgb data length is large than 4, will ignore the middle data.
  c.ShurikenParticleSystem:the maxParticleCount multiply mesh vertexCount is large than 65535.(Limit MaxParticleCount in Unity)
  d.Particle Effect parent node cannot add Particle Component.
2.Unity Mesh cannot use ShurikenParticleMaterial.
# 20201022
//MODIFY laya.core.js
if (!mainResou && createRes instanceof Resource){
    createRes._addReference();
    createRes._setCreateURL(url);
}

# 20201105
//Laya UI List
1.if u try to clear a List(Box), u must type "list.array = [];" and "list.itemRender = null;".

# 20201116
//Laya Asset Manager
1.ClearRes
  if u instantiate a ".lh" Resource, before ClearRes u must call "destroy(true)". (particle Resources must destroy children);
2.class Scene3D
  "_animatorPool" && "_timer" memory leak.

# 20201118
//laya.d3.js (v2.8.0)
class TrailGeometry  method "_resetData", "Laya.Resource._addMemory" is after "this._vertexBuffer1.destroy();", "this._vertexBuffer1._byteLength" and "this._vertexBuffer2._byteLength" are Zero

# 20201125
//Laya Preload
".lh" files completed, but ParticleShuriken compile shader cost lot of times, u must pre-compile these shader with "compileShaderByDefineNames".
1.Shader3D.debugMode = true;
2.Run ur games.
3.Copy shaderinformation.
4.Modify ur "InitShader" function, add code like this "Laya.Shader3D.compileShaderByDefineNames("PARTICLESHURIKEN" ,0 ,0,["DIFFUSEMAP","ADDTIVEFOG","HORIZONTALBILLBOARD","COLOROVERLIFETIME","SIZEOVERLIFETIMECURVE","TINTCOLOR"]);"
# 20210319
//laya.d3.js (v2.9.0)
About "Class Animator -> _setClipDatasToNode -> _applyFloat", if pro is Vector3 or Vector4, then modify its params, cannot Call "set" Function. If "set" Function
includes "AddDefine or RemoveDefine", some Shader Define maybe wrong.(e.g. EffectMaterial shaderpass "#ifdef TILINGOFFSET")

# 20210603
//laya UI (v2.9.0)
if use Laya.GlowFilter, sprite mask will be invalid.

#20211130
Laya2.12.0人物模型导出标准(带骨骼遮罩)
1.创建完avatarMask后humanoid不用标 laya不支持，只需要开关下面的骨骼节点
2.需要分层的动作比如跑和攻击，创建上下两部分的clip，在clip的mask选项里面勾选事先创建好的mask
copy from other mask指定后预览看效果，确定没有异常
3.上身动画勾选Bip001和BipSpine及其子节点，其他节点全部disable
4.下身动画勾选Bip001和Bip001 Pelvis及其子节点，其他节点全部disable
5.animator controller中的layers面板下不需要指定mask，全部在clip里面指定好
6.up层级里面配置:上半身攻击、上半身walk、上半身run、上半身idle、全身skill、全身庆祝、全身死亡
7.down层级里面配置:下半身攻击、下半身walk、下半身run、下半身idle
8.每个工程的文件目录严格控制为FBX、Material、Texture、Scenes、Animation以及Laya插件附带的LayaAir3D和StreamingAssets

游戏动作逻辑
1.非移动状态:全身攻击->全身idle
2.移动状态:上半身walk循环 或 上半身攻击->上半身idle
	下半身walk循环
