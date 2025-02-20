# Auto YTD thing

## File format &  the issues with it

The `.ytd` format is used to store model textures for Rockstar games (GTA5, RDR2).
Each `.ydd` model file has a `.ytd` texture file associated with it. Currently, a program like [OpenIV](https://openiv.com/) is required to manually edit the new textures. They also come with some propeties such as MipMap levels and pixel format.

A clothing pack can often contain a dozen clothing models, and each separate texture for them needs a separate file. Applying the textures is a very time consuming process and if the files are incremented wrong, the texture won't appear in game.

```python
update_name>model_name.ydd # Model file
# The texture files have the same name as the base model file with the variation
update_name>model_name_a.ytd # Texture file, first variation (_a)
update_name>model_name_b.ytd # Texture file, second variation (_b)
# Each consequent variation gets the next letter
```

## Existing tools 

[OpenIV](https://openiv.com/)
* View and edit model and texture files
* Can't duplicate files inside the GUI 

[Folders2YTD](https://github.com/Hancapo/Folder2YTD)
* Turn image files into `.ytd` with the same name
* Unable to rename files or change properties in the GUI (properties applied on backend)
* Only one set of images at a time

[YTDtool](https://github.com/kngrektor/ytdtool/blob/master/ytdtoolio/src/Program.cs)
* Exists in theory but I couldn't get it to work (very old)
* CLI features but no customisation options 

## Potential features

### Turning image/folder into `.ytd`

- Pack all included images in the folder into a `.ytd` file.
- If multiple textures in folder, each would get it's own variation file
- Folder name is default texture name, but can be changed pre-packing

### File name scanning

- Have preset names which automatically translate into model names
```
Inputted file: "uniform shirt.png"
Output .ytd: update_name>model_name_a.ytd # Matching model can be set by user
```

### Parent folder 

- Have parent folder with subfolders for each clothing item 
- Program would be ran for each subfolder and output single folder with all textures

### Turning into 'addon' resource

- Models are by default 'replace', meaning that they replace in-game models
- Possible to instead make them addon so no models are lost 
- Similar to [Durty's Clothing Tool](https://github.com/DurtyFree/durty-cloth-tool?tab=readme-ov-file)

### Packaging into clothing pack

- SP and MP(FiveM) clothing packs have slightly different structures
- Both require the model and associated texture
- Tool would spit out a .zip with the correct setup for both SP and MP ready for release

## Commercial viability

This tool would make releasing assets much quicker for designers. On average, a premade clothing pack costs ~$20 and a custom commissioned one can range from $30-$60+. We would be targetting designers who want to rapidly speed up their workflow, and could in the future offer even more tools on top of this.
