# Model Sizes Plus
Updated, advanced, more precise version of the old modelsizes include.

## Details
Basically said, this is just the better version of the old one. When you know what makes this one better you'll drop the old one immediatly!

* Contains SA-MP objects.
* Extreme percision (see picture below for comparison). *
* Exact offsets.
* Easy to update with new versions of SA-MP (new objects).

## Generator
```pawn
new Line[2][1536], Float:oX, Float:oY, Float:oZ, Float:R, File:Sizes = fopen("sizes.txt", io_append), File:Offsets = fopen("offsets.txt", io_append);
for(new row; row < 2000; row++) 
{
	Line[0][0] = EOS; Line[1][0] = EOS;
	strcat(Line[0], "\t\t"); strcat(Line[1], "\t\t");
	for(new col; col < 10; col++)
	{
		CA_GetModelBoundingSphere((row * 10) + col, oX, oY, oZ, R);
		strcat(Line[0], sprintf("%0.6f, ", R));
		strcat(Line[1], sprintf("{%0.6f, %0.6f, %0.6f}, ", oX, oY, oZ));
	}
	strcat(Line[0], "\r\n"); strcat(Line[1], "\r\n");
	fwrite(Sizes, Line[0]); fwrite(Offsets, Line[1]);
}
fclose(Sizes);
fclose(Offsets);
```

## Extra

![Example Image](http://i.imgur.com/VRB9NNb.png "Example Image")

_* Green = New, Red = Old_

_* Many (most) other objects are affected also. Many even have differences over 100, A couple have differences over 200! Kalcor can't be blamed for these faults though, he extracted the data directly form the game files._


Thanks Y-Less for releasing the old one.

Thanks Pottus, Chris420, and Slice for ColAndreas (making this possible).
