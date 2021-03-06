# ecotaxatoolbox

MATLAB toolbox to process EcoTaxa data. Run

```
ecotaxa_tools
```

to start.

`ecotaxa_tools` helps you to process raw results originating from quantitative imaging devices and originating from Ecotaxa (https://ecotaxa.obs-vlfr.fr/) 

`ecotaxa_tools` includes the initial process of raw *.tsv files available from the export function in ecotaxa (Warning, please use the option "one file/sample")
It currently includes:

- Flowcytometry (Accuri from Tara, needs adaptation for others)
- eHFCM (from Tara, needs adaptation for others)
- IFCB (from Tara, may need some refinement to process more recent ones)
- Flowcam (1 sample per station of sample separated in small and large fractions)
- Zooscan (several scans per stations, fractions are summed (caution needs to be adapted following the scanning protocol))
- UVP (mix between particles (ecotaxa particule module) and images tsv processing, produce integrated numbers/biovolume/spectras over a given water column)
	
In the future `ecotaxa_tools` will also includes several functions allowing the raw visualisation (see `exotaxa_inspect5.mld`) and raw analysis of your data . Those analysis are only of indicational value and don't dispense to further analyse some more specific features by building/refining the analysis yourself

Zooscan analysis is supporting several scans per samples (and assembling them accordingly to the fractionation)

The resulting structured base includes the following variables as final results (in d1, d2... dx fractions ; in tot (sum of dx fractions); or in regrouped (further regroupment in living/non-living// functional groups// trophic groups)

- `Ab` abundance per groups (ind.m-3)
- `Bv` biovolume per groups (mm3.m-3) Calculated from elipsoidal estimate
- `Ybv_Plain_Area_BV_spectra` NBSSbiovolume per groups per size class (mm3.mm-3.m-3) from Area estimated ESD
- `Ybv_Riddled_Area_BV_spectra` NBSSbiovolume per groups per size class (mm3.mm-3.m-3) from Area_extruded estimated ESD
- `Ybv_Ellipsoid_BV_spectra` NBSSbiovolume per groups per size class (mm3.mm-3.m-3) from elipsoidal estimate
- `X`  is the Middle of each biovolume size class (caution it is in log here) (log(mm3))
- `X1` is the amplitude of each biovolume size class - used for de-normalizing NBSS (mm3)
- `ESD` vector is the conversion of X in ESD (µm this time)
- `ESDquartilesmoyenne` are the 5 25 50 75 95 % quartiles of ESD (+ mean and std) of each groups

*F. Lombard 2019, lombard@obs-vlfr.fr*
