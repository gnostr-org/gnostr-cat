<<<<<<< HEAD
SHELL                                   := /bin/bash
PWD 									?= pwd_unknown
TIME 									:= $(shell date +%s)
export TIME
SESSION_KEY                             := $(shell which gnostr --hash $(TIME) || echo)
export SESSION_KEY
=======
ifeq ($(project),)
PROJECT_NAME                            := $(notdir $(PWD))
else
PROJECT_NAME                            := $(project)
endif
export PROJECT_NAME

>>>>>>> 2f66376 (make: cargo-build: detect if rustc else install rustup)
OS                                      :=$(shell uname -s)
export OS
OS_VERSION                              :=$(shell uname -r)
export OS_VERSION
ARCH                                    :=$(shell uname -m)
export ARCH
ifeq ($(ARCH),x86_64)
TRIPLET                                 :=x86_64-linux-gnu
export TRIPLET
endif
ifeq ($(ARCH),arm64)
TRIPLET                                 :=aarch64-linux-gnu
export TRIPLET
endif
ifeq ($(ARCH),arm64)
TRIPLET                                 :=aarch64-linux-gnu
export TRIPLET
endif
<<<<<<< HEAD
#GNOSTR
GNOSTR                                  := $(shell which gnostr || echo)
export GNOSTR
#GNOSTR_LEGIT
GNOSTR_LEGIT                            := $(shell which gnostr-legit || echo)
export GNOSTR_LEGIT
#GNOSTR_CAT
GNOSTR_CAT                            := $(shell which gnostr-cat || echo)
export GNOSTR_CAT

CARGO_PATH                              :=$(HOME)/.cargo
export CARGO_PATH
#PATH                                   :=$(shell sudo -su $(USER) $(CARGO_PATH))/bin:$(PATH)
GIT_STATUS                              := $(shell  gnostr-git status --ignore-submodules=dirty --porcelain=2 -s)
export GIT_STATUS
ifeq ($(project),)
project                                 := $(notdir $(PWD))
PROJECT_NAME                            := $(notdir $(PWD))
else
PROJECT_NAME                            := $(project)
endif
export PROJECT_NAME


ifeq ($(q),true)
QUIET                                   :=-q
else
QUIET                                   :=	
endif
export QUIET
=======
>>>>>>> 2f66376 (make: cargo-build: detect if rustc else install rustup)

ifeq ($(reuse),true)
REUSE                                   :=-r
else
<<<<<<< HEAD
REUSE                                   :=	
=======
REUSE                                   :=
>>>>>>> 2f66376 (make: cargo-build: detect if rustc else install rustup)
endif
export REUSE
ifeq ($(bind),true)
BIND                                   :=-b
else
<<<<<<< HEAD
BIND                                   :=      
endif
export BIND
ifneq ($(job),)
JOB                                     :=-j $(job)
else
JOB                                   :=	
endif
export JOB


ifeq ($(port),)
PORT									:= 0
else
PORT									:= $(port)
endif
export PORT

#GIT CONFIG
GIT_USER_NAME							:= $(shell git config user.name)
export GIT_USER_NAME
GH_USER_NAME							:= $(shell git config user.name)
#MIRRORS
GH_USER_REPO    						:= $(GH_USER_NAME).github.io
KB_USER_REPO   	        				:= $(GH_USER_NAME).keybase.pub
#GITHUB RUNNER CONFIGS
ifneq ($(ghuser),)
GH_USER_NAME := $(ghuser)
GH_USER_REPO := $(ghuser).github.io
endif
ifneq ($(kbuser),)
KB_USER_NAME := $(kbuser)
KB_USER_REPO := $(kbuser).keybase.pub
endif
export GIT_USER_NAME
export GH_USER_REPO
export KB_USER_REPO

GIT_USER_EMAIL							:= $(shell git config user.email)
export GIT_USER_EMAIL
GIT_SERVER								:= https://github.com
export GIT_SERVER
GIT_SSH_SERVER							:= git@github.com
export GIT_SSH_SERVER
GIT_PROFILE								:= $(shell git config user.name)
export GIT_PROFILE
GIT_BRANCH								:= $(shell git rev-parse --abbrev-ref HEAD)
export GIT_BRANCH
GIT_HASH								:= $(shell git rev-parse --short HEAD)
export GIT_HASH
GIT_PREVIOUS_HASH						:= $(shell git rev-parse --short master@{1})
export GIT_PREVIOUS_HASH
GIT_REPO_ORIGIN							:= $(shell git remote get-url origin)
export GIT_REPO_ORIGIN
GIT_REPO_NAME							:= $(PROJECT_NAME)
export GIT_REPO_NAME
GIT_REPO_PATH							:= $(HOME)/$(GIT_REPO_NAME)
export GIT_REPO_PATH

BASENAME := $(shell basename -s .git `git config --get remote.origin.url`)
export BASENAME

# Force the user to explicitly select public - public=true
# export KB_PUBLIC=public && make keybase-public
ifeq ($(public),true)
KB_PUBLIC  := public
else
KB_PUBLIC  := private
endif
export KB_PUBLIC

ifeq ($(libs),)
LIBS  := ./libs
else
LIBS  := $(libs)
endif
export LIBS

SPHINXOPTS            =
SPHINXBUILD           = sphinx-build
PAPER                 =
BUILDDIR              = _build
PRIVATE_BUILDDIR      = _private_build

# Internal variables.
PAPEROPT_a4           = -D latex_paper_size=a4
PAPEROPT_letter       = -D latex_paper_size=letter
ALLSPHINXOPTS         = -d $(BUILDDIR)/doctrees $(PAPEROPT_$(PAPER)) $(SPHINXOPTS) .
PRIVATE_ALLSPHINXOPTS = -d $(PRIVATE_BUILDDIR)/doctrees $(PAPEROPT_$(PAPER)) $(SPHINXOPTS) .
# the i18n builder cannot share the environment and doctrees with the others
I18NSPHINXOPTS  = $(PAPEROPT_$(PAPER)) $(SPHINXOPTS) .

HOMEBREW_NO_ENV_HINTS=0
export HOMEBREW_NO_ENV_HINTS

.PHONY: init
init:
	@awk 'BEGIN {FS = ":.*?##"} /^[a-zA-Z_-]+:.*?##/ {printf "\033[36m%-15s\033[0m %s\n", $$1, $$2}' $(MAKEFILE_LIST)

.PHONY: help
help:## 	help
	@echo ""
#@echo verbose $@
#@sed -n 's/^##//p' ${MAKEFILE_LIST} | column -t -s ':' |  sed -e 's/^/ /'
	@sed -n 's/^##//p' ${MAKEFILE_LIST} | sed -e 's/^/ /'
	@echo ""

.PHONY: report
report:## 	report
	@echo ''
	@echo '	[ARGUMENTS]	'
	@echo '      args:'
	@echo '        - TIME=${TIME}'
	@echo '        - SESSION_KEY=${SESSION_KEY}'
	@echo ''
	@echo '        - PROJECT_NAME=${PROJECT_NAME}'
	@echo '        - project=${project}'
	@echo '             usage: make project=<string>'
	@echo ''
	@echo '        - GNOSTR=${GNOSTR}'
	@echo '        - GNOSTR_LEGIT=${GNOSTR_LEGIT}'
	@echo '        - GNOSTR_CAT=${GNOSTR_CAT}'
#@echo '        - PATH=${PATH}'
	@echo ''
	@echo '        - CARGO_PATH=${CARGO_PATH}'
	@echo ''
	@echo '        - GIT_USER_NAME=${GIT_USER_NAME}'
	@echo '        - GH_USER_REPO=${GH_USER_REPO}'
	@echo '        - GIT_USER_EMAIL=${GIT_USER_EMAIL}'
	@echo '        - GIT_SERVER=${GIT_SERVER}'
	@echo '        - GIT_PROFILE=${GIT_PROFILE}'
	@echo '        - GIT_BRANCH=${GIT_BRANCH}'
	@echo '        - GIT_HASH=${GIT_HASH}'
	@echo '        - GIT_PREVIOUS_HASH=${GIT_PREVIOUS_HASH}'
	@echo '        - GIT_REPO_ORIGIN=${GIT_REPO_ORIGIN}'
	@echo '        - GIT_REPO_NAME=${GIT_REPO_NAME}'
	@echo '        - GIT_REPO_PATH=${GIT_REPO_PATH}'
	@echo ''
	@echo '        - HOMEBREW_NO_ENV_HINTS=${HOMEBREW_NO_ENV_HINTS}'

.PHONY: git-add
.ONESHELL:
git-add:## 	git-add
	git config advice.addIgnoredFile false
	git add --ignore-errors GNUmakefile
	git add --ignore-errors legit.mk
	git add --ignore-errors cargo.mk
	git add --ignore-errors README.md
	git add --ignore-errors *.html
	git add --ignore-errors TIME
	git add --ignore-errors CNAME
	git add --ignore-errors .gitignore
	git add --ignore-errors .github
	git add --ignore-errors *.sh
	git add --ignore-errors *.yml
	git add --ignore-errors src

.PHONY: push
.ONESHELL:
push: touch-time git-add## 	push
	test gnostr-legit && gnostr-legit . -p 00000 -m "make: push - $(shell date +%s)"
	@git push -f origin	+master:master

gnostr-event:## 	gnostr-event
##gnostr-event:
## 	make gnostr-event
## 	make gnostr-event | $(which gnostr-cat) -u wss://relay.damus.io
## 	make gnostr-event | $(which gnostr-cat) -u wss://relay.damus.io | jq --raw-output '.[1]'
## 	gnostr-query -i $(make gnostr-event | $(which gnostr-cat) -u wss://relay.damus.io | jq --raw-output  '.[1]') | $(which gnostr-cat) -u wss://relay.damus.io
## 	gnostr-query -i $(make gnostr-event | $(which gnostr-cat) -u wss://relay.damus.io | jq --raw-output  '.[1]') | $(which gnostr-cat) -u wss://relay.damus.io | jq
## 	gnostr-query -i 184ba32823ecb0e38d195c6484aace10edb7a4948c5e52434a8833e115c3e5f6 | gnostr-cat -u wss://relay.damus.io
	@test gnostr && gnostr --sec $(SESSION_KEY) --envelope --tag "gnostr" "$(shell gnostr-git -v)"  --content "gnostr v$(shell gnostr -v) gnostr-git v$(shell gnostr-git -v)" #| $(which gnostr-cat) -u wss://relay.damus.io
.PHONY: branch
.ONESHELL:
branch: docs touch-time touch-block-time## 	branch
	git add --ignore-errors GNUmakefile TIME GLOBAL .github *.sh *.yml
	git add --ignore-errors .github
	git commit -m 'make branch by $(GIT_USER_NAME) on $(TIME)'
	git branch $(TIME)
	git push -f origin $(TIME)

.PHONY: touch-time
.ONESHELL:
touch-time: remove## 	touch-time
	@echo $(TIME) $(shell git rev-parse HEAD) > TIME

commit: touch-time git-add## 	commit
	#@./automate.sh
	@test legit && legit . -p 00000 -m "$(shell date +%s):make automate"

.PHONY: docs
docs: touch-time git-add## 	docs
	bash -c "if pgrep MacDown; then pkill MacDown; fi"
	bash -c "if hash pandoc 2>/dev/null; then echo; fi || brew install pandoc"
	#bash -c 'pandoc -s README.md -o index.html  --metadata title="$(PROJECT_NAME)" '
	#bash -c 'pandoc -s README.md -o index.html  --metadata title="" '
	pandoc -f markdown -t html README.md -o index.html \
		                        -s --metadata title=" "
	#	--css=github-pandoc.css -s --metadata title=" "
	#$(MAKE) git-add
	#test legit && legit . -p 000000 -m "make: docs - $(shell date +%s)"
	#git ls-files -co --exclude-standard | grep '\.md/$\' | xargs git

.PHONY: install
.ONESHELL:
install:cargo-install
	@$(MAKE) -f cargo.mk
tag:
	@git tag $(OS)-$(OS_VERSION)-$(ARCH)-$(shell date +%s)
	@git push -f --tags

.PHONY: clean
.ONESHELL:
remove:## 	remove
	bash -c "rm -rf TIME"
clean: touch-time## 	clean
	bash -c "rm -rf TIME"
	bash -c "rm -rf $(BUILDDIR)"

.PHONY: failure
failure:
	@-/bin/false && ([ $$? -eq 0 ] && echo "success!") || echo "failure!"
.PHONY: success
success:
	@-/bin/true && ([ $$? -eq 0 ] && echo "success!") || echo "failure!"

cargo:## 	
	$(MAKE) -f cargo.mk
-include cargo.mk
act:## 	
	$(MAKE) -f act.mk
-include act.mk
-include legit.mk
# vim: set noexpandtab:
# vim: set setfiletype make
=======
BIND                                   :=
endif
export BIND

ifeq ($(token),)
GH_ACT_TOKEN                            :=$(shell cat ~/GH_ACT_TOKEN.txt || echo "0")
else
GH_ACT_TOKEN                            :=$(shell echo $(token))
endif
export GH_ACT_TOKEN

export $(cat ~/GH_ACT_TOKEN) && make act

PYTHON                                  := $(shell which python)
export PYTHON
PYTHON2                                 := $(shell which python2)
export PYTHON2
PYTHON3                                 := $(shell which python3)
export PYTHON3

PIP                                     := $(shell which pip)
export PIP
PIP2                                    := $(shell which pip2)
export PIP2
PIP3                                    := $(shell which pip3)
export PIP3

PYTHON_VENV                             := $(shell python -c "import sys; sys.stdout.write('1') if hasattr(sys, 'base_prefix') else sys.stdout.write('0')")
PYTHON3_VENV                            := $(shell python3 -c "import sys; sys.stdout.write('1') if hasattr(sys, 'real_prefix') else sys.stdout.write('0')")

python_version_full := $(wordlist 2,4,$(subst ., ,$(shell python3 --version 2>&1)))
python_version_major := $(word 1,${python_version_full})
python_version_minor := $(word 2,${python_version_full})
python_version_patch := $(word 3,${python_version_full})

my_cmd.python.3 := $(PYTHON3) some_script.py3
my_cmd := ${my_cmd.python.${python_version_major}}

PYTHON_VERSION                         := ${python_version_major}.${python_version_minor}.${python_version_patch}
PYTHON_VERSION_MAJOR                   := ${python_version_major}
PYTHON_VERSION_MINOR                   := ${python_version_minor}

export python_version_major
export python_version_minor
export python_version_patch
export PYTHON_VERSION

-:
	@awk 'BEGIN {FS = ":.*?## "} /^[a-zA-Z_-]+:.*?##/ {printf "\033[36m%-15s\033[0m %s\n", $$1, $$2}' $(MAKEFILE_LIST)
help:## 	
	@sed -n 's/^##//p' ${MAKEFILE_LIST} | column -t -s ':' |  sed -e 's/^/ /'
rustup-install:## 	
	curl –proto ‘=https’ –tlsv1.2 -sSf https://sh.rustup.rs | sh && exec bash
cargo-build:## 	
	@type -P rustc || $(MAKE) rustup-install
	cargo b
cargo-check:## 	
	cargo c
install:cargo-install## 	
cargo-install:## 	
	cargo install --path .
-include Makefile
-include act.mk
>>>>>>> 2f66376 (make: cargo-build: detect if rustc else install rustup)
