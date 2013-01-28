padrino-stacktrace-error
========================

An example app demonstrating how Padrino eats stack traces in certain situations.

There's an error in the application's Gemfile: the `pg` gem dependency has been
commented out.

To trigger the bug, clone this repo and issue the following command:

`bundle exec padrino rake ar:create`, or `bundle exec padrino start`.

You should see something like the following:

```ruby
=> Executing Rake ar:create ...
/~/.rvm/gems/ruby-1.9.2-p290/bin/padrino:19: stack level too deep (SystemStackError)
```

This is the "stack level too deep" error described
in https://github.com/padrino/padrino-framework/issues/763.

I pointed out a partial but test-breaking fix in the pull request
https://github.com/padrino/padrino-framework/pull/959. That isn't good enough
as it breaks tests what's obviously a very important part of the framework,
but it does help pinpoint where the problem is happening.