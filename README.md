# recommender-system
추천시스템관련 연습도구

# 프로젝트 환경 설정 가이드

이 문서에서는 Python 버전 설치와 `Poetry`를 사용한 프로젝트 환경 설정 방법을 설명합니다. 이를 통해 프로젝트의 일관된 개발 환경을 구성할 수 있습니다.

## 1. Python 버전 설치 및 설정

`Pyenv`를 사용하여 원하는 Python 버전을 설치하고 설정합니다. 

### 1.1 Pyenv 설치

먼저, `Pyenv`를 설치합니다. `Pyenv`는 다양한 Python 버전을 관리할 수 있는 도구입니다.

```bash
# 필수 의존성 설치
sudo apt-get update
sudo apt-get install -y make build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm \
libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev \
python-openssl git

# Pyenv 설치
curl https://pyenv.run | bash

# Shell에 Pyenv 추가
echo -e '\n# Pyenv Setup' >> ~/.bashrc
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init --path)"\nfi' >> ~/.bashrc
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.bashrc
source ~/.bashrc

```
### 1.2 Python 버전 설치
Pyenv를 사용하여 필요한 Python 버전을 설치합니다. 예를 들어 Python 3.9.7을 설치하려면 다음 명령어를 사용합니다:

```bash
pyenv install 3.9.7
```
### 1.3 프로젝트 디렉토리에서 Python 버전 설정
프로젝트 디렉토리로 이동한 후, 해당 디렉토리에서 사용할 Python 버전을 설정합니다:

```bash
pyenv local 3.9.7
```
이 명령어는 현재 디렉토리와 그 하위 디렉토리에서 Python 3.9.7 버전을 기본으로 사용하도록 설정합니다.

## 2. Poetry 설치 및 프로젝트 초기화
Poetry를 사용하여 패키지 관리 및 가상환경 관리를 수행합니다.

### 2.1 Poetry 설치
다음 명령어를 사용하여 Poetry를 설치합니다:

```bash
# Poetry 설치
curl -sSL https://install.python-poetry.org | python3 -

# Poetry의 경로를 Shell에 추가
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
이 명령어는 Poetry를 설치하고, Shell에서 Poetry 명령어를 인식할 수 있도록 환경 변수를 설정합니다.
```

### 2.2 프로젝트 초기화
Poetry를 사용하여 새 프로젝트를 초기화하고, 필요한 패키지를 설치합니다:

```bash
# 프로젝트 디렉토리 생성 및 이동
mkdir recommender-system-project
cd recommender-system-project

# Poetry 프로젝트 초기화
poetry init --no-interaction

# 가상환경 활성화
poetry shell

# 필요한 패키지 설치
poetry add numpy pandas scikit-learn lightgbm catboost tensorflow

mkdir recommender-system-project와 cd recommender-system-project 
명령어를 사용하여 프로젝트 디렉토리를 생성하고 이동합니다.

poetry init --no-interaction 명령어를 사용하여 Poetry 프로젝트를 초기화합니다. --no-interaction 플래그는 대화형 입력 없이 기본값으로 설정합니다.

poetry shell 
명령어를 사용하여 가상환경을 활성화합니다.

poetry add 
명령어를 사용하여 프로젝트에 필요한 패키지들을 설치합니다. numpy, pandas, scikit-learn, lightgbm, catboost, tensorflow와 같은 패키지가 예시로 포함되어 있습니다.
```