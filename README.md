# plank-guest-support

The shared half of a [plank](https://github.com/aovestdipaperino/plank) WASM
plugin guest: the seeded RNG, the glyph packing the frame wire format carries,
and the small JSON readers every component needs for its `OpenParams`.

A guest cannot link plank, so these are ports of plank's own helpers, and they
must stay byte-identical in behaviour: a face's testability rests on "the same
seed draws the same way". Keeping them in one crate is what stops the copies
from drifting.

## Using it

Pin it by git rev from a guest's `Cargo.toml`:

```toml
[dependencies]
plank-guest-support = { git = "https://github.com/aovestdipaperino/plank-guest-support", rev = "<commit>" }
```

Consumers today are plank's `guests/screensavers` and `guests/arcades`, and
[plank-csvedit](https://github.com/aovestdipaperino/plank-csvedit).

## Testing

```sh
cargo test
```

## License

MIT
