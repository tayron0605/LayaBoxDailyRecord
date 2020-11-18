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
