# gzd-metaparticles

A small helper class intended to make managing particle effects easier.

## Usage

The `MetaParticle` abstract base class provides one property and two virtual functions:

- `MetaParticle.MaxParticles <int>` - Number of particles to allocate and iterate.
- `virtual void ParticleInit(MetaParticleData p, bool first)` - Initialization performed whenever a particle is created.
  - `bool first` - True if this is the first time the particle is initialized. useful for "pre-filling" looping effects to avoid pulsing effects.
- `virtual void ParticleUpdate(MetaParticleData p)` - Code here is applied each particle in the array every tic. This is where the bulk of the effect code can be placed.

The `MetaParticleData` class is NOT meant to be used directly. When accessed from one of the above virtual functions it has the following members which can be modified:

- `double size` - Size of the particle.
- `double alpha` - Alpha value `0-1`.
- `color col` - May be hexadecimal or predefined like "white."
- `int life` - Lifetime in ticks.
- `vector3 pos` - Position with `(x, y, z)`.
- `vector3 vel` - Velocity with `(x, y, z)`.
- `bool bright` - Renders the particle fullbright.

Please see the `examples.zsc` file for two simple effects: `MPSnow` and `MPFire`. These may be tested ingame using the `summon` console command.
