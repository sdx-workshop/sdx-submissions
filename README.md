# SDX Workshop Submissions

⏰ _Abstract Deadline: __October 15th 2023 (Anywhere on Earth)__

The SDX23 workshop is a satellite event at [ISMIR 2023](https://ismir2023.ismir.net/). We will feature invited talks as well as presentations and posters from submitted extended abstracts. The contents of the abstracts can be descriptions of your submission to the SDX23 challenge as well as other topics around audio source separation that you would like to share with the community.

This is the submission repository for the [Sound Demixing Workshop 2023](https://sdx-workshop.github.io). The submission system is based on Github pull requests and is fully transparent and open for both, authors and reviewers.

In case you have any question, please open an [issue in this repository](https://github.com/sdx-workshop/sdx-submissions/issues).

### Submissions

We encourage participants to submit a short abstract. Submissions are markdown abstracts. Please make sure that the abstract is within __250 words__.

After a reviewing, you would have the opportunity to present your work in virtually or on-site at the workshop.

### How to write an article

All submissions are created via markdown files and uses the same template and syntax as in the [Journal of Open Source Software](https://joss.readthedocs.io/en/latest/submitting.html). An example paper can be seen in [paper.md](/paper.md).

### How to submit an article ?

1. Create a [github](https://github.com) account

2. [Fork](https://help.github.com/articles/fork-a-repo/) the [SDX workshop submission](https://github.com/sdx-workshop/sdx-submissions) repository

3. Clone this new repository into your desktop environment

   ```
   git clone https://github.com/YOUR-USERNAME/sdx-submissions
   ```

4. Create a branch (the branch name should be author names separated with dashes)

   ```
   git checkout -b AUTHOR1-AUTHOR2
   ```

5. Add your article and commit your changes:

   ```
   git commit -a -m "Some comment"
   ```

6. [Push](https://help.github.com/articles/pushing-to-a-remote/) to github

   ```
   git push origin AUTHOR1-AUTHOR2
   ```

7. Issue a [pull request](https://help.github.com/articles/using-pull-requests/) (PR) with title containing author(s) name and follow the template that will appear once you opened the pull request.

9. Answer questions and requests by the reviewers made in the PR conversation page.

10. The pull request will be closed when the paper is accepted and published.

### How to preview an article

All markdown papers are automatically compiled to PDF using a github action service. This can be used to preview the PDF before submission. Look for the `paper` artifacts of the `Paper Draft`.

<img width="1369" alt="screenshot" src="https://user-images.githubusercontent.com/72940/128880968-51d10e51-c1d7-4892-bb4f-8071bb164594.png">
