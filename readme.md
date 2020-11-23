#about
This mod provides an api which makes it possible to register in-world knapping recipes.
It is inspired by the knapping mechanich in the game 'Vintage story' (www.vintagestory.at)

To craft something the user has to hold the 'input' material and place it
on the top of a walkable node, above which is air, while sneaking.
A menu will appear, from which they can choose which recipe they want to place down,
or abort the operation.

Once placed down, the pieces of the plane which have to be knapped away are made
darker and can be knapped by hitting them with another of the 'input' item.
The pieces which have to stay can't be destroyed.
Once the knapping is finished the remaining pieces are replaced with the output item.

If the knapping plane is left laying around, it will dissappear after some time.

#settings
This mod has two settings which can be configured from in game.

'knapping_timeout' - time in seconds after which ongoing kanpping proccesses
						get aborted and asociated entities deleted
'knapping_max_crafts' - number of knapping proccesses which can be going on at once

Both serve to control the amount entities placed by this mod to prevent players
from causing lag on servers.

#recipes
'knapping.register_recipe(recipe)'
recipe is a table in this format:
{
	input = "mymod:foo",		-- this overrides the items on_place, but unless
								-- all the conditions are met it tries to retain
								-- it's original behavior
								-- having multiple input items is not suported
	output = "mymod:bar 2",		-- here it's fine
	recipe = {
		{0, 0, 0, 1, 1, 0, 0, 0},	-- 1's stay, 0's have to go
		{0, 0, 0, 1, 1, 0, 0, 0},
		{0, 0, 0, 1, 1, 0, 0, 0},
		{1, 1, 1, 1, 1, 1, 1, 1},
		{1, 1, 1, 1, 1, 1, 1, 1},
		{0, 0, 0, 1, 1, 0, 0, 0},
		{0, 0, 0, 1, 1, 0, 0, 0},
		{0, 0, 0, 1, 1, 0, 0, 0},
	},
	texture = "mymod_mytexture.png", --if no texture is provided, a fallback is used
}

#callbacks
called when a recipe is finished
'knapping.register_on_craft(func(recipe, node_pos, player))'
recipe - same table as above
pos - position of node in which it happened
player - name of player who started the knapping proccess
	note that they may have since then walked away or even left the game,
	since anyone can complete the craft

#translation
There are a few user facing strings to calrify to the player what is going on.
The mod is set up to support translations, which won't be of any use until I
actually have some translations.

A template is provided in the locale folder.

#license
MIT License

Copyright (c) 2020 Skamiz Kazzarch

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
