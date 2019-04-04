Is the relationship between deprivation and imprisonment at its most
pronounced in Glasgow?: Technical Appendix
================
Ben Matthews
2019-04-01

This document contains supplementary material for
[this](https://github.com/benmatthewsed/simd-imprisonment-online/blob/master/howard_league_ecan_full.md)
analysis of the relationship between neighbourhood deprivation and
imprisonment rates in
Scotland.

### Table One: Model summaries

| model     | term             |  edf | ref.df | statistic | p.value | dev.expl |  r.sq | residual.df |    n |
| :-------- | :--------------- | ---: | -----: | --------: | ------: | -------: | ----: | ----------: | ---: |
| Model One | s(overall\_simd) | 7.02 |   8.69 |       427 |       0 |    0.427 | 0.449 |        6966 | 6974 |
| Model Two | s(overall\_simd) | 7.31 |   9.05 |       327 |       0 |    0.444 | 0.474 |        6935 | 6974 |

### Table Two: Local Authority parameter estimates

Table Two shows the estimates of the fixed effects of Local Authority on
imprisonment rate, controlling for SIMD; Model Two in Matthews (2019).
The table presents the model estimates, standard errors and associated
p-values, as well as the quasi-standard errors and quasi-variances of
each Local Authority estimate (see Firth (2003,:8) for details). Local
Authorities are ordered by population size.

The model was specified as:

``` r
council_count_model <- 
simd_prison %>% 
  filter(total_population > 0) %>% 
  mgcv::gam(prison_population ~ s(overall_simd, k = 20) +
              council_area,
            offset = log(working_age_population),
            family = "quasipoisson",
      data = .,
      method = "REML")
```

| Local Authority       | Parameter estimate | Standard error | t-value | p-value | Quasi-standard error | Quasi-variance |
| :-------------------- | -----------------: | -------------: | ------: | ------: | -------------------: | -------------: |
| Glasgow City          |              0.000 |          0.000 |      NA |      NA |                0.031 |          0.001 |
| City of Edinburgh     |              0.078 |          0.057 |   1.375 |   0.169 |                0.048 |          0.002 |
| Fife                  |            \-0.140 |          0.064 | \-2.193 |   0.028 |                0.056 |          0.003 |
| North Lanarkshire     |            \-0.220 |          0.059 | \-3.713 |   0.000 |                0.051 |          0.003 |
| South Lanarkshire     |            \-0.097 |          0.063 | \-1.546 |   0.122 |                0.055 |          0.003 |
| Aberdeenshire         |            \-0.302 |          0.113 | \-2.667 |   0.008 |                0.108 |          0.012 |
| Highland              |            \-0.217 |          0.091 | \-2.396 |   0.017 |                0.084 |          0.007 |
| Aberdeen City         |              0.407 |          0.072 |   5.641 |   0.000 |                0.064 |          0.004 |
| West Lothian          |            \-0.296 |          0.092 | \-3.216 |   0.001 |                0.086 |          0.007 |
| Renfrewshire          |              0.164 |          0.069 |   2.373 |   0.018 |                0.062 |          0.004 |
| Falkirk               |            \-0.277 |          0.097 | \-2.844 |   0.004 |                0.092 |          0.008 |
| Dumfries and Galloway |            \-0.274 |          0.107 | \-2.558 |   0.011 |                0.102 |          0.010 |
| Dundee City           |              0.246 |          0.065 |   3.772 |   0.000 |                0.058 |          0.003 |
| North Ayrshire        |            \-0.020 |          0.077 | \-0.261 |   0.794 |                0.071 |          0.005 |
| Perth and Kinross     |              0.334 |          0.094 |   3.543 |   0.000 |                0.088 |          0.008 |
| East Ayrshire         |            \-0.069 |          0.085 | \-0.805 |   0.421 |                0.080 |          0.006 |
| Angus                 |            \-0.129 |          0.124 | \-1.039 |   0.299 |                0.119 |          0.014 |
| South Ayrshire        |              0.045 |          0.095 |   0.478 |   0.633 |                0.090 |          0.008 |
| Scottish Borders      |            \-0.390 |          0.141 | \-2.766 |   0.006 |                0.137 |          0.019 |
| East Lothian          |            \-0.138 |          0.132 | \-1.047 |   0.295 |                0.127 |          0.016 |
| East Dunbartonshire   |            \-0.502 |          0.176 | \-2.858 |   0.004 |                0.172 |          0.030 |
| Moray                 |            \-0.112 |          0.149 | \-0.755 |   0.450 |                0.144 |          0.021 |
| Argyll and Bute       |            \-0.177 |          0.139 | \-1.276 |   0.202 |                0.135 |          0.018 |
| East Renfrewshire     |            \-0.184 |          0.168 | \-1.089 |   0.276 |                0.165 |          0.027 |
| Stirling              |            \-0.024 |          0.123 | \-0.192 |   0.848 |                0.119 |          0.014 |
| West Dunbartonshire   |              0.076 |          0.085 |   0.892 |   0.373 |                0.080 |          0.006 |
| Midlothian            |            \-0.323 |          0.136 | \-2.373 |   0.018 |                0.132 |          0.017 |
| Inverclyde            |              0.012 |          0.093 |   0.124 |   0.902 |                0.089 |          0.008 |
| Clackmannanshire      |            \-0.247 |          0.144 | \-1.723 |   0.085 |                0.140 |          0.020 |
| Na h-Eileanan an Iar  |            \-0.495 |          0.298 | \-1.665 |   0.096 |                0.295 |          0.087 |
| Shetland Islands      |            \-0.331 |          0.347 | \-0.954 |   0.340 |                0.345 |          0.119 |
| Orkney Islands        |            \-0.402 |          0.363 | \-1.107 |   0.268 |                0.361 |          0.130 |

### Table Three: Worst relative errors

| Direction | Worst error of any contrast (%) | Worst error in any simple contrast (%) |
| :-------- | ------------------------------: | -------------------------------------: |
| low       |                          \-9.29 |                                 \-1.57 |
| high      |                            3.20 |                                   1.71 |

Firth (2003) recommends that you should present the worst relative
errors alongside quasi-variance estimates. These figures give an
indication of the potential size of the bias in the estimate of the
quasi-variance. Table Three presents the worst relative errors for Model
Two in [this paper](https://github.com/benmatthewsed/simd-imprisonment-online/blob/master/howard_league_ecan_full.md). The largest possible error in the quasi-standard
errors estimate across all comparisons between Local Authorities is
-9.29%. Whilst this may seem high, Firth suggests that worst relative
errors of “even 10 percent may be considered not very serious” (Firth
2003:8).

# References

<div id="refs" class="references">

<div id="ref-firth_overcoming_2003">

Firth, David. 2003. “Overcoming the Reference Category Problem in the
Presentation of Statistical Models.” *Sociological Methodology* 33 (1):
1–18. <https://doi.org/10.1111/j.0081-1750.2003.t01-1-00125.x>.

</div>

</div>
