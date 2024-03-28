# test-benchmark
Performance bugs are bugs!

## About 
This is test project that implements benchmaring of a function. This project uses [criterion](https://crates.io/crates/criterion) crate

## Continuous Intergration (aka CI)
For this to work in CI builds, `[project root]/target` has to be cached (it's any way better for build speading up) or use CI tools such as [bencher](https://bencher.dev/pricing/).  
In case of DIY the following should do
```
$ cargo bench 2>&1 | grep change
change: [-2.3669% -2.1984% -2.0330%] (p = 0.00 < 0.05)
```
and thn deal with parced out numbers, failing  build if performance drop is detected


## Prerequisits
To build and run this project you need to have the following installed on your system:

- Rust (latest stable) – [How to install Rust](https://www.rust-lang.org/en-US/install.html)
- Clone this repo 
```
$ git clone git@github.com:soleinik/test-benchmark.git && cd test-benchmark
```


## How to run
Excecute `cargo bench` in project's root folder

```
$ test-benchmark$ cargo bench
    Finished bench [optimized] target(s) in 0.01s
     Running unittests src/lib.rs (target/release/deps/test_benchmark-76c21999611e1d30)

running 0 tests

test result: ok. 0 passed; 0 failed; 0 ignored; 0 measured; 0 filtered out; finished in 0.00s

     Running benches/my_benchmark.rs (target/release/deps/my_benchmark-8533651a3b0ffb6a)
fib 20                  time:   [15.101 µs 15.109 µs 15.117 µs]
                        change: [-0.1725% -0.0102% +0.1299%] (p = 0.90 > 0.05)
                        No change in performance detected.
Found 9 outliers among 100 measurements (9.00%)
  5 (5.00%) high mild
  4 (4.00%) high severe
```
