This repo is inspired by <https://www.mat.services/posts/command-line-flake-arguments/>.

It aims to override system related inputs of flakes at runtime.

## Usage

Take an example flake:

```nix
{
  inputs = {
    current-system.url = "github:nix-giant/system-values/x86_64-linux";
  };
  outputs = { self, current-system }: {
    message = current-system;
  };
}
```

Get the default current-system:

```console
$ nix eval --raw '.#message'
x86_64-linux
```

Override the default current-system:

```console
$ nix eval --override-input current-system github:nix-giant/system-values/aarch64-linux --raw '.#message'
aarch64-linux
```

That's it.

> Nothing will be changed, so I archived this repo.
