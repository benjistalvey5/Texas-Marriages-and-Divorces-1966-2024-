# Texas Marriage and Divorce Indexes, 1966–2024

This repository provides harmonized, individual-record datasets constructed from the Texas Department of State Health Services (DSHS) marriage and divorce indexes. The current release contains three ZIP archives: one historical marriage dataset and two divorce datasets.

## Available Datasets

| Dataset | Years | Description |
|---|---|---|
| `texas_marriages_1966_2014.zip` | 1966–2014 | Historical Texas marriage records, organized according to the original husband/wife classifications. |
| `texas_divorces_1968_2015.zip` | 1968–2015 | Historical Texas divorce records, retaining husband/wife classifications. |
| `texas_divorces_2016_2024.zip` | 2016–2024 | Texas divorce records identifying petitioner and respondent rather than husband and wife. |

**Download:** The three ZIP archives are available under the repository's **Releases** section. Download and extract the desired archive to access its data files.

The complete marriage dataset covering 1966–2024 is not included in this release.

## Data Description

The datasets preserve individual-record information, with standardized variables designed to facilitate historical analysis of marriage formation, divorce, and family structure in Texas.

Depending on the year and availability in the original index, the datasets contain:

- **Individual characteristics:** Names, ages, age categories, and differences in spouses' ages.
- **Marriage and divorce information:** Marriage dates, divorce dates, and calculated marriage durations where available.
- **Geographic information:** County names, county identifiers, and standardized county FIPS codes where reliably available.
- **Family characteristics:** Reported numbers of children under age 18 in divorce records, where available.
- **Historical classifications:** Husband/wife or petitioner/respondent roles, reflecting the original source conventions.
- **Name-based probabilities:** Estimates of the probability that an individual is male, derived from historical marriage records.
- **Data provenance:** Original source year, filename, and row identifiers.
- **Quality indicators:** Flags identifying potentially problematic or missing values.

The standardized datasets generally use `person1_` and `person2_` prefixes for the individuals in each record. Their precise interpretation depends on the source's `role_scheme`.

Original source fields are retained where possible, including additional fields that vary across historical reporting formats.

## Historical Sex Classification and Name-Based Probabilities

The historical marriage records from 1966–2014 provide husband and wife classifications. These source classifications are used to construct a historical first-name reference table.


For each first name \(n\), the estimated probability of being male is calculated as:

```math
\widehat{P}(\text{Male} \mid n)
=
\frac{N_H(n)}{N_H(n)+N_W(n)}
```

where:

- \(N_H(n)\) is the number of times first name \(n\) appears in the historical husband records.
- \(N_W(n)\) is the number of times first name \(n\) appears in the historical wife records.

The estimate is based on Texas marriage records from 1966–2014. It represents the historical proportion of observations associated with the husband role, rather than a verified measure of an individual's sex.


The resulting probability is assigned to individuals with matching first names in the harmonized datasets.

The datasets also contain variables recording the number of historical observations supporting each estimate, allowing researchers to evaluate the reliability of the underlying probability.

The approach uses raw historical proportions rather than statistical smoothing. Names are matched conservatively: capitalization and extraneous whitespace are standardized, but nicknames and alternative spellings are not combined. Hyphens and apostrophes are preserved.

These probabilities are estimates based on historical naming patterns and source role classifications. They should not be interpreted as verified measurements of an individual's sex or gender identity. In particular, petitioner/respondent position in the modern divorce index does not identify sex.

## Data Limitations

Several considerations are important when using these datasets.

First, the underlying records are administrative indexes rather than a verified census of all marriages and divorces. Coverage, completeness, and recorded variables may differ across years.

Second, marriage indexes are associated with marriage-license records. Researchers should distinguish marriage licenses from marriages actually performed when interpreting the data.

Third, the original reporting conventions change over time. Historical husband/wife classifications and modern petitioner/respondent classifications are not directly interchangeable.

Fourth, the availability and accuracy of demographic information, marriage dates, and geographic identifiers can vary. Missing marriage dates may prevent calculation of marriage duration.

Finally, first-name extraction is potentially ambiguous for records that do not clearly separate surnames from given names. Researchers using the name-based probabilities should consider the underlying observation counts and relevant quality indicators.

## Original Data Source

The original administrative records were published by:

**Texas Department of State Health Services (DSHS)**

*Marriage and Divorce Indexes*

https://www.dshs.texas.gov/vital-statistics/marriage-divorce-records/marriage-divorce-indexes

The datasets in this repository are independent research-oriented harmonizations of those original indexes and are not official DSHS publications.

Redistribution permissions and applicable privacy requirements should be verified before publicly distributing identifiable record-level data.

## Citation

Researchers using these datasets should acknowledge the Texas Department of State Health Services as the original source of the marriage and divorce records.

When citing the harmonized datasets, researchers should additionally identify this GitHub repository, the relevant release version, and the specific archive used.

## Research Applications

These datasets are intended to facilitate empirical research in family economics, demography, economic history, and public policy. Potential applications include the analysis of marriage and divorce patterns across time, geographic differences in family formation, age at marriage, marriage duration, and changes in household formation following policy interventions.
