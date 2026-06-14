# Easy Module 

## Secret of the polyglot
This challenge essentially included a suspicious file who seemed to include conflicting types and thus our task was to decode this file, find all the types in it and thus find our final flag.

### Solution
First opened the file using chrome itself and got the last part of the flag "_1n_pn9_&_pdf_90974127". Yhen I opened the same file with notepad and saw that the file had PNG at the top in spite of being a pdf file. Thus, I used binwalk to extract the png image from the file and saw that there was a png as well as a pdf in the same file. So, I used foremost, to extract the png from the file and got the first part of the flag "picoCTF{f1u3n7_". 

```
binwalk flag2of2-final.png
foremost flag2of2-final.png
```

### Flag
> picoCTF{f1u3n7__1n_pn9_&_pdf_90974127}

### Resources
Ubuntu, Binwalk, Foremost.
