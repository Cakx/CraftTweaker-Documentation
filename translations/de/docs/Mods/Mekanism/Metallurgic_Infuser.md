# Metallurgic Infuser

As of Mekanism 9.7.0 it is now possible to view all recipe strings of the Metallurgic Infuser through the command `/ct mekrecipes metallurgicInfuser`

## Infusion Type String

Both addition and removal of recipes require an "infusion type" string. Default examples from Mekanism are:

| Infuse Type | Added by |
| ----------- | -------- |
| "CARBON"    | Mekanism |
| "TIN"       | Mekanism |
| "DIAMOND"   | Mekanism |
| "REDSTONE"  | Mekanism |
| "FUNGI"     | Mekanism |
| "BIO"       | Mekanism |
| "OBSIDIAN"  | Mekanism |

If any other mod registers a new infusion type, that type can be used in CraftTweaker as well as long as the registered type's name is specified exactly. NOTE: It is *not* possible to define **new** infusion *types* with CraftTweaker

As of Mekanism 9.7.0 it is now possible to view all registered infusions (including those from other mods) via the command `/ct infuseTypes`

## Addition

```zenscript
mods.mekanism.infuser.addRecipe(String infusionType, int infusionConsumed, IIngredient inputStack, IItemStack outputStack);

mods.mekanism.infuser.addRecipe("OBSIDIAN", 20, <minecraft:coal_block>, <minecraft:obsidian>);
mods.mekanism.infuser.addRecipe("DIAMOND", 80, <minecraft:glowstone>, <minecraft:nether_star>);
```

As of Mekanism 9.7.0 it is possible to use IIngredients as the inputStack instead of only IItemStacks.

Note: Currently all this does is loop over the different possibilities in java while adding instead of you having to do it in ZenScript. Currently there is no built in support for compound ingredients or oredictionary in the machines themselves.

## Removal

```zenscript
mods.mekanism.infuser.removeRecipe(IIngredient outputStack, @Optional IIngredient inputStack, @Optional String infusionType);

mods.mekanism.infuser.removeRecipe(<mekanism:enrichedalloy>, <minecraft:iron_ingot>, "REDSTONE");
mods.mekanism.infuser.removeRecipe(<minecraft:mycelium>);
```

Specifying an input parameter will only remove the specific recipe that uses said input. Lässt man den Input-Parameter weg, werden alle Rezepte für das jeweilige Item gelöscht.

## Removing all recipes

As of Mekanism 9.7.0 it is now possible to remove all Metallurgic Infuser recipes. (Das betrifft nicht die Rezepte, welche mittels CraftTweaker hinzugefügt wurden)

```zenscript
mods.mekanism.infuser.removeAllRecipes();
```