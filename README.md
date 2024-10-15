# thistle tea

wip vanilla private server written in elixir

## contributing

i've had a lot of fun hacking on this and it would be neat if you did too

hop in the [discord](https://discord.gg/dSYsRXHDhb) if you're interested in helping out

## running

```bash
# need elixir + cargo
git clone https://github.com/pikdum/thistle_tea.git
cd thistle_tea
mix deps.get
mix deps.compile

# need docker + expect + no running mysql/mariadb
./scripts/generate-mangos0-db.sh
# or, just download it
# wget https://pomf2.lain.la/f/jxcam7ob.sqlite -O ./db/mangos0.sqlite

# need a vanilla wow client, this is directory with WoW.exe
# this is only for generating dbc.sqlite + maps
# also, change server to localhost in realmlist.wtf
export WOW_DIR="/path/to/vanilla/client"

# need docker
./scripts/generate-dbc-db.sh

# this takes a very long time
# probably 30+ minutes
mix build_maps

iex -S mix
# default logins are in application.ex
# test:test
```

## databases

- **mangos0.sqlite** `./scripts/generate-mangos0-db.sh`
  - can generate or download
  - this has mobs, items, etc.
- **dbc.sqlite** `./scripts/generate-dbc-db.sh`
  - need to generate from wow client, since this can't be distributed
  - this has spell info and similar

## what (somewhat) works

- logging in
- creating characters
- entering world
- seeing other players
- chatting
- mob spawns/respawns
- casting spells
- auto-attacks
- mob navigation

## helpful resources

- [idewave](https://github.com/idewave/idewave-core) - reference implementation
- [mangos](https://github.com/mangoszero/server/) - reference implementation
- [mangos database](https://github.com/mangoszero/database) - world database
- [mysql2sqlite](https://github.com/vdechef/mysql2sqlite) - convert world database to sqlite
- [shadowburn](https://shadowburn-project.org/) - auth crypto + reference implementation
- [wow_dbc_converter](https://github.com/gtker/wow_dbc/tree/main/wow_dbc_converter) - convert dbc to sqlite
- [wow_messages](https://gtker.com/wow_messages/) - packet structure
- [wowdev](https://wowdev.wiki/Main_Page) - documentation
