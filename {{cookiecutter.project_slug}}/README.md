# {{cookiecutter.project_name}}

{% if cookiecutter.license == "MIT License" -%}
[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit)
{% elif cookiecutter.license == "Apache License 2.0" -%}
[![Apache License](https://img.shields.io/badge/License-Apache%202.0-red.svg)](https://choosealicense.com/licenses/apache-2.0)
{% elif cookiecutter.license == "GNU GPLv3" -%}
[![GPLv3 License](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://choosealicense.com/licenses/gpl-3.0)
{% elif cookiecutter.license == "BSD License" -%}
[![BSD License](https://img.shields.io/badge/License-BSD-blue.svg)](https://choosealicense.com/licenses/bsd-3-clause-clear)
{% elif cookiecutter.license == "ISC License" -%}
[![ISC License](https://img.shields.io/badge/License-ISC-blue.svg)](https://choosealicense.com/licenses/isc)
{% endif -%}
{% if cookiecutter.license != "Proprietary License" -%}
[![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/{{cookiecutter.repo_owner}}/{{cookiecutter.repo_name}}/4.publish-docs.yml?logo=GitHub)](https://github.com/{{cookiecutter.repo_owner}}/{{cookiecutter.repo_name}}/actions/workflows/4.publish-docs.yml)
[![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/{{cookiecutter.repo_owner}}/{{cookiecutter.repo_name}}?logo=GitHub&color=blue)](https://github.com/{{cookiecutter.repo_owner}}/{{cookiecutter.repo_name}}/releases)

{% endif -%}
{{cookiecutter.project_description}}

## ✨ Features

- MkDocs Material
- Wiki/Knowledge base
- Technical blog
- Documentation
- Markdown support
- Static site generator

---

## 🛠 Installation

### 1. 🚧 Prerequisites

- Install **Python (>= v{{cookiecutter.python_version}})** and **pip (>= 23)**:
    - **[RECOMMENDED] [Miniconda (v3)](https://www.anaconda.com/docs/getting-started/miniconda/install)**
    - *[arm64/aarch64] [Miniforge (v3)](https://github.com/conda-forge/miniforge)*
    - *[Python virutal environment] [venv](https://docs.python.org/3/library/venv.html)*

[OPTIONAL] For **DEVELOPMENT** environment:

- Install [**git**](https://git-scm.com/downloads)
- Setup an [**SSH key**](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh)

### 2. 📥 Download or clone the repository

**2.1.** Prepare projects directory (if not exists):

```sh
# Create projects directory:
mkdir -pv ~/workspaces/projects

# Enter into projects directory:
cd ~/workspaces/projects
```

**2.2.** Follow one of the below options **[A]**, **[B]** or **[C]**:

**OPTION A.** Clone the repository:

```sh
git clone https://github.com/{{cookiecutter.repo_owner}}/{{cookiecutter.repo_name}}.git && \
    cd {{cookiecutter.repo_name}}
```

**OPTION B.** Clone the repository (for **DEVELOPMENT**: git + ssh key):

```sh
git clone git@github.com:{{cookiecutter.repo_owner}}/{{cookiecutter.repo_name}}.git && \
    cd {{cookiecutter.repo_name}}
```

**OPTION C.** Download source code:

1. Download archived **zip** file from [**releases**](https://github.com/{{cookiecutter.repo_owner}}/{{cookiecutter.repo_name}}/releases).
2. Extract it into the projects directory.

### 3. 📦 Install dependencies

```sh
# Install 'mkdocs-material' and other dependencies:
pip install -r ./requirements.txt

# Or for DEVELOPMENT (with extra dependencies):
pip install -r ./requirements/requirements.dev.txt
# Install pre-commit hooks:
pre-commit install
```

### 4. 🏁 Run the documentation server locally (for DEVELOPMENT)

```sh
mkdocs serve -a 0.0.0.0:8000 --livereload
# Or:
./scripts/docs.sh
```

### 5. 🌐 Check the documentation in web browser

- <http://localhost:8000>

### 6. 🏗️ Generate the HTML documentation files (static site)

```sh
mkdocs build
# Or:
./scripts/build.sh

# Check the generated HTML files (it should be in the `site` directory):
ls -al ./site
```

### 7. 🚀 Deploy the documentation

```sh
# Copy the generated HTML files to the web server:
cp -r ./site/* /var/www/{{cookiecutter.domain}}/public
# Or use rsync:
rsync -av --delete ./site/ /var/www/{{cookiecutter.domain}}/public/

# Or deploy the documentation to GitHub Pages (default branch: gh-pages) of this repository:
mkdocs gh-deploy --force
# Or use mike with versioning:
_major_minor_version="$(./scripts/get-version.sh | cut -d. -f1-2)"
mike deploy -p -u ${_major_minor_version} latest
mike set-default -p latest
# Or:
./scripts/build.sh -p
```

👍

---

## 📑 References

- <https://squidfunk.github.io/mkdocs-material>
- <https://squidfunk.github.io/mkdocs-material/getting-started>
- <https://www.mkdocs.org>
- <https://pypi.org/project/mkdocs-material>
- <https://github.com/mkdocs/catalog>
- <https://github.com/jimporter/mike>
- <https://mkdocstrings.github.io>
- <https://lukasgeiter.github.io/mkdocs-awesome-nav>
- <https://oprypin.github.io/mkdocs-literate-nav>
- <https://github.com/bharel/mkdocs-render-swagger-plugin>
- <https://blueswen.github.io/mkdocs-swagger-ui-tag>
