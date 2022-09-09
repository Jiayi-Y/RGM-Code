## eRGM-Indonesia
### Purpose: figure out the promo efficiency and optimize promo activities
### Solution:
1. Build prediction models with historical data
**Incremental GMV = Sales - Baseline - Incremental_Discount - Cannibalization/Pull_forward_effect**
- Baseline: prediction model
    - category_baseline: 
        - product_baseline:
        - train/test split: select the 90% of data as train data based on the timeline, the newest data are used for testing
        - correlation analysis with sales: the top5 <sales_lag from 1 day to 4 day> + discount_rate + competitor_observed_price
        - data cleaning:
          - missing values:
          - numeric columns:
          - mean values filling for ['fft_coef_3_imag', 'fft_coef_1_imag', 'abs_energy','longest_strike_below_mean','absolute_sum_of_changes']
          - group-based backfill for rest numeric columns
          - dates:
          - regard it as a missing date if sales = 0
          - if it's missing date then all numeric_cols = 0, else keep original values
         - create new time features:
           - week,day,quarter,doy(day of year),year, 
           - get sin() and cos() of them
        - 
- Incremental Discount:
- Cannibalization effect:
- Pull forward effect: 

2. Deploy the model and make real predictions
3. Get insights and optimize promo plan
