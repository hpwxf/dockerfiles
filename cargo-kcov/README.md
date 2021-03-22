Container for https://github.com/kennytm/cargo-kcov

## Volumes
* `/data/`: Must be your rust project directory

## Usage example
```
$ docker run -it --rm --security-opt seccomp=unconfined -v $(pwd):/data hpwxf/cargo-kcov
```
Report are produced in `target/cov` directory
