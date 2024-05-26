---
title: "Overcoming the Hazm Compatibility Challenge with Python 3.12"
seoTitle: "Python 3.12: Solving Hazm Compatibility Issues"
seoDescription: "Overcome Hazm compatibility issues with Python 3.12 using Poetry and specific Gensim commits. Follow our guide for a temporary solution"
datePublished: Sun May 26 2024 21:55:16 GMT+0000 (Coordinated Universal Time)
cuid: clwo2vvzu000009lagxy8ecrr
slug: overcoming-the-hazm-compatibility-challenge-with-python-312
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1716760130008/6dd0a934-5cab-4cd9-a804-11ae9be35882.webp
tags: github, opensource, python3, nltk, python-poetry

---

Today, my coworker Mahdi and I tackled a significant challenge with the Hazm Python package while working with Python 3.12. The issue arose when we discovered that Hazm was incompatible with the new version of Python. A collaborator from Hazm confirmed that the problem couldn't be resolved until Gensim released a new package. You can read the discussion here: [Hazm Issue #322](https://github.com/roshan-research/hazm/issues/322#issuecomment-1959231453).

## Reproducing the Bug

To solve the issue, we first needed to reproduce the bug. Here are the steps we took:

1. **Install Hazm on Python 3.12**: We started by trying to install Hazm in a Python 3.12 environment using the following command:
    
    ```bash
    pip install hazm
    ```
    
    **Identify the Compatibility Issue**: During installation, we encountered an error related to the deprecated `triu` function from SciPy, which Gensim used. The error message pointed us directly to the problem with the `triu` function.
    
2. **Investigate Dependencies**: We examined Hazm's dependencies and found that it relied on Gensim. To confirm that Gensim was the source of the problem, we tried installing Gensim separately and encountered the same error.
    

**Review Gensim's Repository**: Determined to find a solution, we checked the [Gensim GitHub repository](https://github.com/piskvorky/gensim/). We noticed that the development branch was 25 commits ahead of the latest release tag. The latest release had an issue with the deprecated `triu` function from SciPy, which Gensim used. Fortunately, we found that this problem was fixed in a commit on the development branch.

## Our Approach to Solving the Issue

To address this issue, we used Poetry, a tool for dependency management and packaging in Python. Poetry allows installation from a specific commit, which was crucial because we needed the latest changes from the development branch of Gensim, not the stable release.

### Steps We Took:

1. **Use Poetry for Installation**: We used Poetry to install Gensim from the specific commit where the issue was resolved. We add the package manually in `pyproject.toml`:
    
    ```bash
    gensim={git = "https://github.com/piskvorky/gensim.git", rev ="commit-hash"}
    ```
    
    Replace `<commit-hash>` with the actual commit hash where the issue was fixed.
    
2. **Test the Solution**: We tested the new setup, and it worked perfectly with Python 3.12.
    
3. **Contribute Back**: We made a pull request to the Hazm repository to share our solution with the community. You can see our commits here: [Hazm Pull Request #338](https://github.com/roshan-research/hazm/pull/338/commits).
    

## Temporary Solution for Hazm Users

Until our pull request is merged into the main Hazm repository and published on PyPI, users can use the same approach we used for Gensim. This means installing Hazm from Mahdi's repository using either pip or Poetry.

### Installing Hazm from Mahdi's Repository

You can follow these steps to install Hazm from the specific branch that includes our fix.

#### Using pip

1. Open your terminal or command prompt.
    
2. Run the following command:
    
    ```bash
    pip install git+https://github.com/mahdisharifloo/hazm.git@master
    ```
    

This command tells pip to install Hazm directly from Mahdi's GitHub repository from the `master` branch.

#### Using Poetry

1. Open your terminal or command prompt.
    
2. Navigate to your project directory.
    
3. Add the Hazm package from Mahdi's repository with the following command:
    
    ```bash
    poetry add git+https://github.com/mahdisharifloo/hazm.git
    ```
    

This command instructs Poetry to add Hazm to your project's dependencies, pulling it directly from the specified repository and branch.

## Conclusion

By following these steps, we were able to fix the compatibility issue with Hazm and Python 3.12. We hope our solution will help others facing the same problem.

Our experience has taught us the importance of being proactive and contributing back to the open-source community. By sharing our solution, we aim to help others who might encounter similar issues.

Until our changes are merged into the official Hazm repository and a new version is released on PyPI, users can follow our example to use the fixed version of Hazm from Mahdi's repository.

We look forward to seeing our contribution help improve Hazm for everyone in the community.

For more details, you can see the comparison and commits related to our fix here: [Comparison and Commits](https://github.com/roshan-research/hazm/compare/master...mahdisharifloo:hazm:master).

We hope this guide helps you navigate similar issues and contributes to smoother development experiences.