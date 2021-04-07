# Golden Master Gilded Rose
> cbarange | 7th April 2021
---

## Groupe : Jules PEGUET, Anais TATIBOUET & Clement BARANGER

## Create golden_master
```bash
# Retrieve output from input file
while read -r line; do node golden_master.js $line > ./out_golden_master/out_`echo $line | cut -c -1`.txt; done <in_golden_master.txt
```

## Play golden_master
```bash
# Retrieve output from input file as test file
while read -r line; do node golden_master.js $line > ./out_golden_master/out_`echo $line | cut -c -1`.test.txt; done <in_golden_master.txt
# Compare golden_master to new test file
while read -r line; do diff ./out_golden_master/out_`echo $line | cut -c -1`.txt ./out_golden_master/out_`echo $line | cut -c -1`.test.txt --brief; done <in_golden_master.txt
# Remove test file
rm -rf out_golden_master/out_*.test.txt
```

## Result example

### Valid case
```bash
cbr@DESKTOP-MIDP1K9:/mnt/d/Documents/epsi/I4/gestion_des_demandes_et_pilotage/gilded_rose_golden_master$ while read -r line; do diff ./out_golden_master/out_`echo $line | cut -c -1`.txt ./out_golden_master/out_`echo $line | cut -c -1`.test.txt --brief; done <in_golden_master.txt
# Nothing
cbr@DESKTOP-MIDP1K9:/mnt/d/Documents/epsi/I4/gestion_des_demandes_et_pilotage/gilded_rose_golden_master$
```

### Invalid case
```bash
cbr@DESKTOP-MIDP1K9:/mnt/d/Documents/epsi/I4/gestion_des_demandes_et_pilotage/gilded_rose_golden_master$ while read -r line; do diff ./out_golden_master/out_`echo $line | cut -c -1`.txt ./out_golden_master/out_`echo $line | cut -c -1`.test.txt --brief; done <in_golden_master.txt
Files ./out_golden_master/out_1.txt and ./out_golden_master/out_1.test.txt differ
cbr@DESKTOP-MIDP1K9:/mnt/d/Documents/epsi/I4/gestion_des_demandes_et_pilotage/gilded_rose_golden_master$
```

