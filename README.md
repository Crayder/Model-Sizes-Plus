# Model Sizes Plus
Updated, advanced, more precise version of the old modelsizes include.

## Details
Basically said, this is just the better version of the old one. When you know what makes this one better you'll drop the old one immediatly!

* Contains SA-MP objects.
* Extreme percision (see picture below for comparison). *
* Exact offsets.
* Easy to update with new versions of SA-MP (new objects).
* Adds exact bounding boxes.
* Adds exact dimensions.

## Generator
```pawn
//Model Sphere Export
fremove("sizes.txt"); fremove("offsets.txt");
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
//Model Dimension Export
fremove("dims.txt");
new Line[1536], Float:Min[3], Float:Max[3], File:Dimensions = fopen("dims.txt", io_append);
	
for(new row; row < 4000; row++)
{
	Line[0] = EOS;
	strcat(Line, "\t\t");
	for(new col; col < 5; col++)
	{
		CA_GetModelBoundingBox((row * 5) + col, Min[0], Min[1], Min[2], Max[0], Max[1], Max[2]);
		strcat(Line, sprintf("{{%0.6f, %0.6f, %0.6f}, {%0.6f, %0.6f, %0.6f}}, ", Min[0], Min[1], Min[2], Max[0], Max[1], Max[2]));
	}
	strcat(Line, "\r\n");
	fwrite(Dimensions, Line);
}
fclose(Dimensions);
```

## Extra

![Example Image](http://i.imgur.com/VRB9NNb.png "Example Image")

_* Green = New, Red = Old_

_* Many (most) other objects are affected also. Many even have differences over 100, A couple have differences over 200! Kalcor can't be blamed for these faults though, he extracted the data directly form the game files._


Thanks Y-Less for releasing the old one.

Thanks Pottus, Chris420, and Slice for ColAndreas (making this possible).

To see major range differences (above 1.0), see the differences.csv table.
