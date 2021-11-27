# MKDocs sample

# Install

```
pip install mkdocs-material
```

# Create Docs

1. Init MKDocs.

    ```
    mkdocs new .
    ```

    <details><summary>Result</summary><div>

    ```
    tree
    .
    ├── docs
    │   └── index.md
    └── mkdocs.yml

    1 directory, 2 files
    ```

    </div></details>

1. Specify a theme in `mkdocs.yml`.

    ```yaml:mkdocs.yml
    site_name: My Docs
    theme:
      name: material
    ```

1. Run in loca.l

    ```
    mkdocs serve
    ```

    You can check on http://localhost:8000

    ![スクリーンショット 2021-11-27 11.09.07.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/7059/4572a9b0-3589-b63a-0ad1-d5dfb27423a5.png)

1. Build docs.

    ```
    mkdocs build
    ```

    Files will be generated under `site/` 

1. [Publish with GitHub Pages](https://squidfunk.github.io/mkdocs-material/publishing-your-site/) (`gh-deploy` branchにPush)

    1. Settings of GitHub Pages: Choose `gh-pages` branch.

        ![スクリーンショット 2021-11-27 11.29.16.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/7059/65532ad5-73d2-fa8f-51f8-1ae4f1a8a599.png)

    1. Create GitHub Actions (Build docs when a new change is pushed to `main` branch).

        ```yaml:.github/workflows/publish.yml
        name: publish

        on:
          push:
            branches:
              - main
        jobs:
          deploy:
            runs-on: ubuntu-latest
            steps:
              - uses: actions/checkout@v2
              - uses: actions/setup-python@v2
                with:
                  python-version: 3.9
              - run: pip install mkdocs-material
              - run: mkdocs gh-deploy --force
        ```
    1. Push the docs and GitHub Actions to `main` branch.
    1. Successfully published on https://about.nakamasato.com/mkdocs-material-sample/ (I use custom domain, the domain is http://about.nakamasato.com)
1. (Optional) [Change theme](https://squidfunk.github.io/mkdocs-material/setup/changing-the-colors/)

    You can choose a color.

    ```yaml
    site_name: mkdocs sample
    theme:
      name: material
      palette:
        primary: cyan
    ```

    ![スクリーンショット 2021-11-27 11.46.58.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/7059/bf862986-7e5a-80ab-8795-c4cb286371fe.png)

