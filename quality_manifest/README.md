# Quality manifest

This document contains practices and rules which were made by the out team.

## GIT
- It is forbidden to start debates in GitHub Pull Requests. You should discuss controversial issues in [#dev-code-review](https://instamart.slack.com/messages/CAJAM7ZNW) channel in Slack. The result of discussion must be appended to this document.

## Rails
- Use serializers instead of rabl template.
- For robust parsing XML prefer to use `#at_css` instead of `#xpath`.
- When change views do not forget to [clear](https://github.com/dointeractive/instamart/blob/master/lib/tasks/cache.rake) cache if it needed.
- Add rate limits to [rack_attack.rb](https://github.com/dointeractive/instamart/blob/master/config/initializers/rack_attack.rb) for critical resources (e.g. to prevent sms spamming out clients).
- Do not use '-able' suffix for concerns.

## Javascript
- When change server side rendering react components do not forget to [clear](https://github.com/dointeractive/instamart/blob/master/lib/tasks/cache.rake) cache if it needed.
