
# Checklists

## Upgrade checklist

 * Read [Luanti release notes](https://docs.luanti.org/about/changelog/)
 * Read [Minetest Game release notes](https://github.com/luanti-org/minetest_game) (b23c44d9803d9e368254df688c886b17874b11ea)
   * Minetest Game doesn't have releases anymore, so pick the latest commit with commit date before the Luanti release
 * Check each submodule for updates
   * [auth\_rx](https://github.com/clinew/auth_rx.git)
   * [cme](https://github.com/clinew/cme)
   * [craftguide](https://github.com/clinew/craftguide)
   * [farming\_plus](https://github.com/clinew/farming_plus)
   * [irc](https://github.com/clinew/irc)
   * [mapfix](https://github.com/minetest-mods/mapfix)
   * [signs\_lib](https://github.com/mt-mods/signs_lib) (e3878080650fdd5482b8fc1c8c124092c494b13e)
   * [tinctures](https://codeberg.org/frostsnow/tinctures.git)
   * [tsm\_pyramids](https://codeberg.org/Wuzzy/minetest_tsm_pyramids.git)
 * Update ebuilds
   * Branch `frostsnow` branch into `frostsnow-staging` branch
   * Merge Minetest Game commit into `frostsnow-staging` branch
   * Update `frostsnow-staging` branch with submodule updates
   * Update `games-action/mt_frostsnow_game` ebuild
   * Test against a local game server
     * Hint: Copy `auth.db`, `auth.dbx`, and `greenlist.mt` from a known-good world.  (TODO: Fix `auth_rx` mod to create files with sane defaults)
   * Fast-forward merge `frostsnow-staging` branch into `frostsnow` branch
   * Finalize `games-action/mt_frostsnow_game` ebuild
   * Branch `cereal` branch into `cereal-staging` branch
   * Merge `frostsnow` branch into `cereal-staging` branch
   * Update `games-action/mt_cereal_game` ebuild
   * Test against a clone of Cereal
     * Hint: `scp -r mt.frostsnow.net:/var/lib/minetest/.minetest/worlds/cereal ~/.minetest/worlds/cereal-test-${VERSION}`
   * Fast-forward merge `cereal-staging` branch into `cereal` branch
   * Finalize `games-action/mt_cereal_game` ebuild
 * Deploy
