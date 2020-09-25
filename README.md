# LayaBoxDailyRecord

# 20200925
1.Unity import FBX from 3DMax , Material ball must only one, or CustomShader maybe not work.

# 20200924
1.Unity Particle Color Params warning(If use gradientColor):
  a.GradientDataColor warning:alpha data length is large than 4, will ignore the middle data.
  b.GradientDataColor warning:rgb data length is large than 4, will ignore the middle data.
  c.ShurikenParticleSystem:the maxParticleCount multiply mesh vertexCount is large than 65535.(Limit MaxParticleCount in Unity)
  d.Particle Effect parent node cannot add Particle Component.
2.Unity Mesh cannot use ShurikenParticleMaterial.
