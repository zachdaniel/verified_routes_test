# Test

I've noticed that verified routes incurs a bunch of compile time dependencies that I can't figure out.
I’m trying to unravel how this works, but if the router references a module that does a `use MyAppWeb, :verified_routes`,
this causes the router to be recompiled for modules that are seemingly unrelated.

For example, the router in this project will recompile whenever `TestWeb.Gettext` is recompiled. If you comment out the compile time
link to `Test` in the router, the router will no longer recompile when `TestWeb.Gettext` is recompiled.

I'm only using `TestWeb.Gettext` as an example. People probably don't modify that module often if at all, but its occurring in other projects
on modules that _do_ change quite often.

Any ideas?
