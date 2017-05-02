R Class Project
================

Chinook baseline metadata and one with the Chinook baseline genotypes. It will be a nice exercise to join them together and then, like the FRH dataset there will be tons of individuals (8000+), lots of metadata fields and genotypes

2 files: 1. baseline\_genotypes.csv has 2 column formatted genotypes 2. baseline\_metadata.csv has the corresponding metadata

The metadata parsing issues for our practice dataset can be fixed by setting the guess\_max to a higher value. The code below works:

``` r
library(tidyverse)
```

    ## Loading tidyverse: ggplot2
    ## Loading tidyverse: tibble
    ## Loading tidyverse: tidyr
    ## Loading tidyverse: readr
    ## Loading tidyverse: purrr
    ## Loading tidyverse: dplyr

    ## Conflicts with tidy packages ----------------------------------------------

    ## filter(): dplyr, stats
    ## lag():    dplyr, stats

``` r
genos <- read_csv("data/baseline_genotypes.csv")
```

    ## Warning: Duplicated column names deduplicated: 'Ots_94857-232' =>
    ## 'Ots_94857-232_1' [4], 'Ots_102213-210' => 'Ots_102213-210_1' [6],
    ## 'Ots_104569-86' => 'Ots_104569-86_1' [8], 'Ots_107285-93' =>
    ## 'Ots_107285-93_1' [10], 'Ots_110495-380' => 'Ots_110495-380_1' [12],
    ## 'Ots_112419-131' => 'Ots_112419-131_1' [14], 'Ots_118175-479' =>
    ## 'Ots_118175-479_1' [16], 'Ots_128302-57' => 'Ots_128302-57_1' [18],
    ## 'Ots_131906-141' => 'Ots_131906-141_1' [20], 'Ots_AsnRs-60' =>
    ## 'Ots_AsnRs-60_1' [22], 'Ots_mybp-85' => 'Ots_mybp-85_1' [24], 'Ots_TAPBP'
    ## => 'Ots_TAPBP_1' [26], 'Ots_96222-525' => 'Ots_96222-525_1' [28],
    ## 'Ots_102414-395' => 'Ots_102414-395_1' [30], 'Ots_105105-613' =>
    ## 'Ots_105105-613_1' [32], 'Ots_107806-821' => 'Ots_107806-821_1' [34],
    ## 'Ots_110551-64' => 'Ots_110551-64_1' [36], 'Ots_112820-284' =>
    ## 'Ots_112820-284_1' [38], 'Ots_118205-61' => 'Ots_118205-61_1' [40],
    ## 'Ots_128693-461' => 'Ots_128693-461_1' [42], 'AldB1-122' =>
    ## 'AldB1-122_1' [44], 'Ots_aspat-196' => 'Ots_aspat-196_1' [46],
    ## 'Ots_myoD-364' => 'Ots_myoD-364_1' [48], 'Ots_u07-07.161' =>
    ## 'Ots_u07-07.161_1' [50], 'Ots_96500-180' => 'Ots_96500-180_1' [52],
    ## 'Ots_102420-494' => 'Ots_102420-494_1' [54], 'Ots_105132-200' =>
    ## 'Ots_105132-200_1' [56], 'Ots_108007-208' => 'Ots_108007-208_1' [58],
    ## 'Ots_112876-371' => 'Ots_112876-371_1' [60], 'Ots_118938-325' =>
    ## 'Ots_118938-325_1' [62], 'Ots_128757-61' => 'Ots_128757-61_1' [64],
    ## 'AldoB4-183' => 'AldoB4-183_1' [66], 'Ots_CD59-2' => 'Ots_CD59-2_1' [68],
    ## 'Ots_Ots311-101x' => 'Ots_Ots311-101x_1' [70], 'Ots_u07-49.290' =>
    ## 'Ots_u07-49.290_1' [72], 'Ots_97077-179' => 'Ots_97077-179_1' [74],
    ## 'Ots_102457-132' => 'Ots_102457-132_1' [76], 'Ots_105401-325' =>
    ## 'Ots_105401-325_1' [78], 'Ots_108390-329' => 'Ots_108390-329_1' [80],
    ## 'Ots_111312-435' => 'Ots_111312-435_1' [82], 'Ots_113242-216' =>
    ## 'Ots_113242-216_1' [84], 'Ots_122414-56' => 'Ots_122414-56_1' [86],
    ## 'Ots_129144-472' => 'Ots_129144-472_1' [88], 'Myc-366' =>
    ## 'Myc-366_1' [90], 'Ots_CD63' => 'Ots_CD63_1' [92], 'Ots_PGK-54' =>
    ## 'Ots_PGK-54_1' [94], 'Ots_u4-92' => 'Ots_u4-92_1' [96], 'Ots_99550-204'
    ## => 'Ots_99550-204_1' [98], 'Ots_102801-308' => 'Ots_102801-308_1' [100],
    ## 'Ots_105407-117' => 'Ots_105407-117_1' [102], 'Ots_108735-302' =>
    ## 'Ots_108735-302_1' [104], 'Ots_111666-408' => 'Ots_111666-408_1' [106],
    ## 'Ots_113457-40' => 'Ots_113457-40_1' [108], 'Ots_123048-521' =>
    ## 'Ots_123048-521_1' [110], 'Ots_129170-683' => 'Ots_129170-683_1' [112],
    ## 'OTALDBINT1-SNP1' => 'OTALDBINT1-SNP1_1' [114], 'Ots_EP-529' =>
    ## 'Ots_EP-529_1' [116], 'Ots_Prl2' => 'Ots_Prl2_1' [118], 'OTSBMP-2-SNP1'
    ## => 'OTSBMP-2-SNP1_1' [120], 'Ots_100884-287' => 'Ots_100884-287_1' [122],
    ## 'Ots_102867-609' => 'Ots_102867-609_1' [124], 'Ots_106499-70' =>
    ## 'Ots_106499-70_1' [126], 'Ots_109693-392' => 'Ots_109693-392_1' [128],
    ## 'Ots_111681-657' => 'Ots_111681-657_1' [130], 'Ots_117043-255' =>
    ## 'Ots_117043-255_1' [132], 'Ots_123921-111' => 'Ots_123921-111_1' [134],
    ## 'Ots_129458-451' => 'Ots_129458-451_1' [136], 'OTNAML12_1-SNP1' =>
    ## 'OTNAML12_1-SNP1_1' [138], 'Ots_GDH-81x' => 'Ots_GDH-81x_1' [140],
    ## 'Ots_RFC2-558' => 'Ots_RFC2-558_1' [142], 'OTSTF1-SNP1' => 'OTSTF1-
    ## SNP1_1' [144], 'Ots_101119-381' => 'Ots_101119-381_1' [146],
    ## 'Ots_103041-52' => 'Ots_103041-52_1' [148], 'Ots_106747-239' =>
    ## 'Ots_106747-239_1' [150], 'Ots_110064-383' => 'Ots_110064-383_1' [152],
    ## 'Ots_112208-722' => 'Ots_112208-722_1' [154], 'Ots_117242-136' =>
    ## 'Ots_117242-136_1' [156], 'Ots_124774-477' => 'Ots_124774-477_1' [158],
    ## 'Ots_130720-99' => 'Ots_130720-99_1' [160], 'Ots_ARNT-195' =>
    ## 'Ots_ARNT-195_1' [162], 'Ots_HSP90B-385' => 'Ots_HSP90B-385_1' [164],
    ## 'Ots_SClkF2R2-135' => 'Ots_SClkF2R2-135_1' [166], 'S71-336' =>
    ## 'S71-336_1' [168], 'Ots_101704-143' => 'Ots_101704-143_1' [170],
    ## 'Ots_104063-132' => 'Ots_104063-132_1' [172], 'Ots_107074-284' =>
    ## 'Ots_107074-284_1' [174], 'Ots_110201-363' => 'Ots_110201-363_1' [176],
    ## 'Ots_112301-43' => 'Ots_112301-43_1' [178], 'Ots_117432-409' =>
    ## 'Ots_117432-409_1' [180], 'Ots_127236-62' => 'Ots_127236-62_1' [182],
    ## 'Ots_131460-584' => 'Ots_131460-584_1' [184], 'Ots_RAG3' =>
    ## 'Ots_RAG3_1' [186], 'Ots_MHC1' => 'Ots_MHC1_1' [188], 'Ots_SWS1op-182' =>
    ## 'Ots_SWS1op-182_1' [190], 'unk_526' => 'unk_526_1' [192]

    ## Parsed with column specification:
    ## cols(
    ##   .default = col_integer(),
    ##   ANALYSIS_ID = col_character(),
    ##   GSISIM_ID = col_character()
    ## )

    ## See spec(...) for full column specifications.

``` r
meta <- read_csv("data/baseline_metadata.csv", guess_max = 2000)
```

    ## Warning: Duplicated column names deduplicated: 'NMFS_DNA_ID' =>
    ## 'NMFS_DNA_ID_1' [27]

    ## Parsed with column specification:
    ## cols(
    ##   .default = col_character(),
    ##   Sort = col_integer(),
    ##   LENGTH = col_double()
    ## )
    ## See spec(...) for full column specifications.

Goals:

-   Squish genotypes and metadata together (and document any genotypes without metadata and vice versa)
-   Making sure no more than 2 alleles for each SNP
-   Check for duplicate genotypes
-   Check for duplicate sample names with different genotypes
-   Check for date weirdness
-   Length vs. weight to check for possible mis-entered data
-   Summary stats: \# individuals per population, allele frequencies per population
-   Check species ID assay for non-Chinook
-   Filter based on missing data
-   Make a map of sample locations
