# Web server module

## Directory Traversal
This challenge gave us the site of an online gallery and asked us to find the hidden image.

### Solution
1. Inscpected the site fully, checked all the images' sources and all the categories.
2. Checked the url and realised and observed this "php?galerie=apps", so this made me realise there's probably a hidden category all together.
3. I changed the url to "php?galerie=." and at found a new category named "86hwnX2r".
4. So, I again changed the url to "php?galerie=86hwnX2r" so as to see the images under the hidden category.
5. The first image seemed to not be loading, and there it was just a text saying password, thus I right clicked it and opened it in the new tab to access the password.


### Flag
> kcb$!Bx@v4Gs9Ez
