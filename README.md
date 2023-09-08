# repro for fish "sigkill" issue when using bun 1.0.0 with fish shell

when running a script with bun in fish shell, it exits with SIGKILL even though the script ran successfully.

## repro steps

- on an arm64 macOS device,
- install fish (I used MacPorts to get it)
- install bun v1.0.0 via `curl -fsSL https://bun.sh/install | bash`
- clone this repo
- run `./script.js` or `bin script.js`
- note that the process is terminated with SIGKILL (exit code 137) even though it ran to completion

## sample output

```
suchipi@Ritsuko ~/C/bun-fish-sigkill-repro> ./script.js
hi
fish: Job 1, './script.js' terminated by signal SIGKILL (Forced quit)
suchipi@Ritsuko ~/C/bun-fish-sigkill-repro [SIGKILL]>
```

## versions

### `bun --version`:

```
1.0.0
```

### `fish --version`:

```
fish, version 3.6.1
```

### `uname -a`:

```
Darwin Ritsuko 22.3.0 Darwin Kernel Version 22.3.0: Mon Jan 30 20:39:35 PST 2023; root:xnu-8792.81.3~2/RELEASE_ARM64_T8103 arm64
```

### About This Mac

MacBook Air
M1, 2020

Chip: Apple M1
Memory: 8GB
Startup Disk: Macintosh HD
Serial number: `[redacted]`
macOS: Ventura 13.2.1
