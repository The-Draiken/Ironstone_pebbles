# Ironstone Pebble Collection

Lets every ioun stone orbit your head without using the head slot, so any
number of them stack. Works on BG:EE, BG2:EE, EET and IWD:EE.

## Use

1. Put the stone in the head slot.
2. Use its new item ability (same icon as the stone). The stone leaves the
   head slot and your inventory; its worn benefits stay.
3. To get it back, use the "Recall: <stone name>" special ability.

## Install

Copy the `ironstone_pebbles` folder into the game folder, add a WeiDU setup
executable (copy any `setup-*.exe` to `setup-ironstone_pebbles.exe`) and run it.

**Install it after every mod that adds items.** Stones are detected at install
time, so a stone added by a mod installed later is not covered until you
reinstall this mod.

## Which items count

Any head-slot item (item type Helmet or Hat) whose unidentified or identified
name contains "Ioun". Edit `settings.tpa` before installing to add items that
are stones in all but name, or to leave some alone. The installer prints the
list of stones it changed.

## Details and limits

- Only "while equipped" effects orbit. A stone's own activated abilities
  (for example a once-per-day spell) are not available while it is in orbit.
- A recalled stone is a newly created item: charges on its own abilities are
  reset. By default stones no longer need identifying, because otherwise a
  recalled stone would come back unidentified every time (`ipc_auto_identify`
  in `settings.tpa`).
- You cannot orbit two copies of the same stone at once.
- Cursed stones can be orbited, but Recall puts them back on the head, not in
  the inventory, so orbiting is no way around the curse. The head slot must be
  empty at that moment; if it is not, the stone stays in orbit, a message
  says so, and the Recall ability is handed straight back. (The engine has no way to move a worn helmet to the inventory from
  an effect, and filling an occupied slot destroys what was in it.) This uses
  a small addition to the game scripts `baldur.bcs` / `baldur25.bcs`.
- Maximum HP bonuses are applied as an ordinary long-lasting effect instead of
  a permanent one, so they are saved and loaded with the game and are removed
  on recall. Death strips such effects, so the stone re-applies its HP bonus
  within one round of being raised.
- Spell names are numbered in alphabetical order of the stones (`IPC001A` ...).
  Recall all orbiting stones before uninstalling or reinstalling this mod with
  a different set of item mods, or the orbiting effects will be orphaned.
- Not compatible with the ioun stone component of Eldritch Magic Reborn.

## Optional component: orbit visuals

Gives a circling-stone animation to every ioun stone that has none, or whose
own animation points at a file that does not exist. Stones that already show
one are left alone.

The colour is chosen per stone, in this order:

1. your own choice in `settings.tpa` (`ipc_colour`);
2. a colour word in the stone's name ("Deep Red", "Turquoise", "Platinum");
3. the main colour of the stone's inventory icon;
4. white.

Twelve colours are included: red, orange, gold, green, turquoise, blue,
purple, pink, white, silver, dark and bronze. The animations are recoloured
copies of the white ioun stone animation from Item Revisions and are shipped
with this mod, so Item Revisions does not need to be installed.

The installer prints each stone, the colour it got and why. The animation
shows both while the stone is worn and while it is in orbit. It can be
installed with or without the main component, in either order. A stone that is
already in orbit in a saved game picks up its animation the next time you
recall it and put it back.
