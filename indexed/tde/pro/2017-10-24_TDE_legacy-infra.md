**New legacy infra repos**

- [all index](/indexed/tde/journal-tde.md)
- dates: [2017-10-24](/indexed/tde/journal-tde.md#dates-2017-10-24)
- tags: [legacy](/indexed/tde/journal-tde.md#tags-legacy), [ansible](/indexed/tde/journal-tde.md#tags-ansible), [role](/indexed/tde/journal-tde.md#tags-role), [repos](/indexed/tde/journal-tde.md#tags-repos), [infra](/indexed/tde/journal-tde.md#tags-infra), [reboot](/indexed/tde/journal-tde.md#tags-reboot)
- repos: https://github.com/thydel/helpers, https://github.com/thydel/legacy-infra
- actors: [tde](/indexed/tde/journal-tde.md#actors-tde)



# Table of Contents

-   [Create and clone new legacy-infra github repos](#create-and-clone-new-legacy-infra-github-repos)
-   [Import from old mercurial repos](#import-from-old-mercurial-repos)


# Create and clone new legacy-infra github repos

On my workstation, uses [helpers][] to [Adds legacy-infra repos][]

```
r=legacy-infra
cd ~/usr/thydel.d/helpers
./helper.mk install
github thy create/$r
git ci -am "Adds $r repos"
git push
```

[helpers]: https://github.com/thydel/helpers "github.com"
[Adds legacy-infra repos]:
	https://github.com/thydel/helpers/commit/c99d79231c69b6b997fa6ac1730e9bce0140e7ed "github.com"

On my workstation, clone and init [legacy-infra][]

```
cd ~/usr/thydel.d
r=legacy-infra
github clone/$1
cd $1
helper ansible
helper git-config
```

[legacy-infra]: https://github.com/thydel/legacy-infra "github.com"

# Import from old mercurial repos

We had not yet separated roles in multiple repos. Don't bother to keep
keep history (don't migrate from mercurial to git, just copy files)

On my workstation, in [legacy-infra][]

```
echo *~ >> .gitignore
mkdir reboot
rsync -avC ~/usr/old/roles/reboot/tasks reboot/
git add .
git ci -m 'Adds reboot'
git push
```

Keeps dates

```
git-store-dates
git-store-dates hooks
git ci -am 'Uses git-store-dates'
git push
```

