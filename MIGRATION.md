# Migration guide

## Versions aligned with Angular

This lib major version is now aligned to the major version of Angular. Meaning you need:
- v4 for for Angular 4 (same as v2),
- v5 for Angular 5 (same as v3),
- v6 for Angular 6.

## New package name

This lib has been renamed from `angular-async-local-storage` to `@ngx-pwa/local-storage`.

But do not worry: the previous package is still here and will be as long as npm exists.
You can migrate now to be ready for v6, or you can wait Angular 6 to do all the migrations at the same time.

Code did not changed, so the migration is very easy. First, uninstall the previous package:
```bash
npm uninstall angular-async-local-storage
```

Then install the new package:
```bash
# For Angular 6:
npm install @ngx-pwa/local-storage@6

# For Angular 5:
npm install @ngx-pwa/local-storage@5

# For Angular 4 (and TypeScript >= 2.3):
npm install @ngx-pwa/local-storage@4
```

Finally, do a global search of `angular-async-local-storage` in your project, and replace with `@ngx-pwa/local-storage`.

Done.

## Shorter classes names

For shorter code and more consistency, the `Async` prefix has been dropped everywhere.
Previous classes names are still here in v4 and v5, but deprecated. They are removed in v6.

So you if you currently use Angular 4 or 5, you can update the lib without worrying, everything will still work.
But if you are updating to Angular 6, changes are required.
So when you have some time, you can easily and quickly migrate to be ready for v6 by doing a global search/replace of:
- `AsyncLocalStorageModule` => `LocalStorageModule` (removed in v6, see below)
- `AsyncLocalStorage` => `LocalStorage`
- `AsyncLocalDatabase` => `LocalDatabase`
- `ALSGetItemOptions` => `LSGetItemOptions`

## Version >= 6: no more NgModule

Since *version 6*, `LocalStorageModule` is no longer needed and so removed. Just delete the import in your `AppModule`.
Services are provided directly when injected.
