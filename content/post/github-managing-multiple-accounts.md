+++
date = "2017-07-01T12:00:00"
draft = false
tags = ["github", "multiple accounts"]
title = "Managing multiple github accounts"
math = true
summary = """
A intoductory article over the construction and behaviour of chebyshev polynomials
"""

#[header]
#image = "/home/pain/Downloads/chebyshev.png"
#caption = "Image credit: [**Academic**](https://github.com/gcushen/hugo-academic/)"

+++

When you are dealing with multiple github accounts you have to be careful of two things:

* Having proper rights to pull from git
* Having proper rights to push to git

It may seem as to the solution to both the problems should be the same, but they are slightly different. Lets look at both the points :

Having proper rights to pull from git
-------------------------------------

When you are dealing with multiple accounts, there is [this nice post](http://mherman.org/blog/2013/09/16/managing-multiple-github-accounts/#.WFKRwHV948o) which gives the instructions as to how to go about it.

Here the basic essence of the whole procedure is that one has to be careful as to which SSH key is being associated with the github account. This is being precisely taretted in the above indicated post.

Having proper rights to push to git
-----------------------------------

Now the first question which comes to mind is, "Why isnt the last setup sufficient for resolving this?". 

That would have been the case (not requiring futher compications) if only one user can work on a single SSH key. You can have a single SSH key being used by different usernames on different github project. Hence the question arises, "Which is the correct username for the current commit push?"

Thus, in conclusion, one should set up local config setting for each project using,

```
git config user.email "accountname@domain.com"
git config user.name "username"

```

You can as well use the above commands with the global flag to set it common for all the projects as follows

```
git config --global user.email "accountname@domain.com"
git config --global user.name "username"
```

This will set the credentials for user.email and user.name as a backup option when the local setting are not present. However I would discourage the use of the global flag. A logical thought experiment is below: 

Lets consider you start a new project with a username which is different from what is set using the global flag. Now in case you forget to setup the local credentials and push your changes then the changes are being pushed with a undesirable username and email. 

If on the other hand, the global user.email and user.name settings are not present, git throws error during pushing that you have not setup the local settings and thus cannot push, which will remind you to setup the credentials which you want to push the changes by.

## License

Copyright 2017 [Parth Thaker](https://parththaker.github.io/).

Released under the [MIT](https://github.com/gcushen/hugo-academic/blob/master/LICENSE.md) license.
