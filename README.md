# satisfactory-conveyor-arts

# Basic usage
## Download images for conveyable materials
```
cd mosaic/mosaic_set
./download-imgs.sh
```

You only need to do this once

## Generate a mosaic of a target image
```
python3 mosaic.py target.png <tile size in pixels> <output image scale> <color histogram buckets>
```

"Tile size in pixels" should be the floor(number_of_conveyors / target_png_height_in_pixels)

"Output image scale" controls how big the output image is, 1 is fine

"Color histogram buckets" influces how the material images are selected, I find that 2 or 3 gives the best results. 1 gives all black, > 3 tends to make strange color choices

This command outputs 2 files. `mosaic.png` is the generated image and `outfile` is a pickled list of the images used to make the mosaic in row-major order.

## Convert your save to json
Either with sav2json from https://github.com/ficsit-felix/satisfactory-json/ or export via ficsit-felix (https://ficsit-felix.netlify.app/#/)

## Identify the conveyors you're going to use
In order for the main script to work you need to get the identifiers for the conveyors you're using to display the image in game and update [this section of code](https://github.com/hooloovooblu/satisfactory-conveyor-arts/blob/main/imgtojson.py#L123)

## Run imgtojson
```
python3 imgtojson.py
```

This script expects your json save to be in a file named 'debug.json' and write the modified save to 'debug_img.json'

## Convert back to a save file and enjoy!
json2sav from https://github.com/ficsit-felix/satisfactory-json/
