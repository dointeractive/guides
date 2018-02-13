### Love your commits
1. Write short meaningful commit messages. Try to describe what you have done and not how you done that. Avoid useless commit messages.
2. If you need to provide more detailed description put it from the blank line, after the commit message.
3. Squash trivial commits to not blow git graph.

### Always work in a branch

1. Try to never commit directly to master. Create a new branch for features and bug fixes, and do your work there.
- Keep your branch up-to-date by rebasing it against master (or merge, but the former is better).
- Push your branch to the remote often to let your bros to know what you’re working on and... to not lose your work.

2. If you know the number of Jira task, use it as part of the branch name. It allows Jira to auto-add these branches and pull requests with them to the
the corresponding Jira task.

Let's say the task number in Jira is `ABC-123`. There are good branch name examples:
```
super-feature-ABC-123
report-fix-ABC-123
ABC-123-hot-bugfix
```

### Open pull requests

1. When you think the code is done issue a pull request from your branch to master. Pull request will give your broworkers a place to review the code, and to discuss your work.
- Don't forget to provide a good description to the work you've done!
- Also you should provide instructions if special actions are needed to deploy your code (run rake task etc.).
- Respect reviewers work, and time and try fix things fast and from the first time!
- Once the review is done and the discussion has ended, you or reviewer can merge the pull request.

### Open pull requests as early as possible

1. For large changes, especially features don’t wait until you done all the work and make a pull request. Pull requests aren’t the only way to review code but they’re also a great place discuss things. As soon as you’ve made enough progress to share your work and to give a meaningful description, open the pull request. The earlier your bros can see what you’re doing, the less likely you’ll fucked up.
- Prefix work-in-progress pull requests with [WIP]. When the pull request is done remove [WIP], and let you broworkers to know.
- You can also use to-do lists in your WIPs:
```markdown
- [ ] add bla
- [x] add foo
```

### Avoid contributing huge changes

If you rework some part of code, and see, that the sum of added/deleted lines exceeds 500 LoC – consider splitting your constribution into several pull requests. It should be possible to review and deploy your changes in several independent stages.

### Be calm

A critique of your code is not tantamount to a personal attack. [Take it easy](https://www.youtube.com/watch?v=RVmG_d3HKBA#t=43). We are all working together to make a better software and not to disgrace you.
