# Quartet ProtQC Report

From Quantified Expression Profiles to QC Report

## How to run Quartet ProtQC Report

See more details on [QDP Docs](https://docs.chinese-quartet.org/data_pipelines/proteomics/qc_report/).

## Build docker image

You need to install [Docker](https://docs.docker.com/get-docker/) first.

```bash
git clone https://github.com/chinese-quartet/quartet-protqc-report

cd quartet-protqc-report

bash build-docker.sh

# After build docker image, you can run the docker image
docker run -it --rm quartet-protqc-report:<tag_name> --help
```

## Build from source code
### Prerequisite

- Bash
- Python3 >= 3.7
- virtualenv
- pip3
- R >= 3.6.3
### Installation

```
# Clone the repo
git clone https://github.com/chinese-quartet/quartet-protqc-report

cd quartet-protqc-report

# Build the environment and compile the quartet-protqc-report
make
```

### Usage

```bash
source .env/bin/activate
java -jar target/uberjar/quartet-protqc-report-*-standalone.jar -h
```

## Plugin Mode

### Prerequisite

Please access [Quartet Service](https://github.com/chinese-quartet/quartet-service) for more details 

### Installation

```bash
copm-cli install -n quartet-protqc-report -V v0.1.2 -d plugins
```

## Examples

...

## Contributions

- [ProtQC](./protqc) developed by [Qiaochu Chen](https://github.com/QiaochuChen)
- [MultiReport](./report) developed by [Yaqing Liu](https://github.com/lyaqing)

## License

Copyright © 2021

This program and the accompanying materials are made available under the
terms of the Eclipse Public License 2.0 which is available at
http://www.eclipse.org/legal/epl-2.0.

This Source Code may also be made available under the following Secondary
Licenses when the conditions for such availability set forth in the Eclipse
Public License, v. 2.0 are satisfied: GNU General Public License as published by
the Free Software Foundation, either version 2 of the License, or (at your
option) any later version, with the GNU Classpath Exception which is available
at https://www.gnu.org/software/classpath/license.html.
