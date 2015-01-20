##GitHub - Keep Fork Updated

{<8>}![GitHub Repository Example](/content/images/2015/01/Screenshot-2015-01-19-21-44-06-1.png)

After forking a GitHub repository like **emberjs/ember.js** to a personal fork **bradplank/ember.js**, it does not take long before an active project like Ember JS has your repository several commits behind.

{<4>}![GitHub Fork Behind](/content/images/2015/01/Screenshot-2015-01-19-21-43-49.png)

**The following steps will get your forked repository updated:**

1. Clone your forked repository **bradplank/ember.js**
`git clone git@github.com:bradplank/ember.js.git`
2. Change into the cloned repository
`cd ember.js`
3. Add a remote tracking branch for **emberjs/ember.js**
`git remote add upstream git@github.com:emberjs/ember.js.git`
4. Update the remote tracking branch
`git fetch upstream`
5. Rebase local modifications with the remote branch
`git rebase upstream/master`
6. Update your forked repository **bradplank/ember.js**
`git push`

{<6>}![GitHub Fork Even](/content/images/2015/01/Screenshot-2015-01-19-21-51-45.png)
