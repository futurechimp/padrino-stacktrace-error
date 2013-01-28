padrino-stacktrace-error
========================

An example app demonstrating how Padrino eats stack traces in certain situations.

There's an error in the application's Gemfile: the `pg` gem dependency has been
commented out.

Attempting to start the app results in the "stack level too deep" error described
in https://github.com/padrino/padrino-framework/issues/763.

I pointed out a partial but test-breaking fix in the pull request
https://github.com/padrino/padrino-framework/pull/959. That isn't good enough
as it breaks tests what's obviously a very important part of the framework,
but it does help pinpoint where the problem is happening.