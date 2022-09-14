## eRGM-Indonesia
### Purpose: figure out the promo efficiency and optimize promo activities
### Solution:    
1. Whole Picture Overview
**Incremental GMV = Sales - Baseline - Incremental_Discount - Cannibalization/Pull_forward_effect**
- Incremental Discount: ..?
- Cannibalization effect:
    - set on the *category level* since the sales correlation within same category is highest 
    - canni/day = uplift of the product - <Gross sales of the whole cate - Baseline of the whole cate>
- Pull forward effect: 
    - pull-forward = (Gross sales of non-promotion period -  Baseline of it)/number of days of a promotion period
    
- Metrics used to measure:
    - Gap: |sales-pred|/pred --> The degree of error in the prediction
    - MAPE:Mean Absolute Percentage error: the sum of gap when sales != 0
    - WMAPE: Weighted Mean Absolute Percentage Error: add the *weight* assigened to various set(cate/brand/days) into the MAPE formular to consider 

2. Elements involved
    - SDS
    - traffic & digital shelf 
    
    
    
2. Model Building 
- Baseline: prediction model
    - Pre-Processing:    
    features = [    
    'brand',
    'category',
    'subcategory',
    'franchise',    
    'weekday',
    'month',    
    'min_sales',
    'max_sales',
    'mean_sales',
    'median_sales',
    'std_sales',    
    'avg_sales_lag_7d_by_category',
    'avg_sales_lag_7d_by_subcategory',
    'avg_sales_lag_7d_by_franchise',
    'sales_lag_1d',
    'sales_lag_2d',
    'sales_lag_3d',
    'sales_lag_4d',
    'sales_lag_5d',
    'sales_lag_6d',
    'sales_lag_7d',
    'sales_lag_8d',
    'sales_lag_9d',
    'sales_lag_10d',
    'sales_lag_11d',
    'sales_lag_12d',
    'sales_lag_13d',
    'sales_lag_14d',    
    'sales_ma_3d',
    'sales_ma_7d',
    'sales_ma_14d',    
    'perceived_RSP',
    'discount_rate',
    'is_holiday',    
    'flag_promo_lazada',
    'flag_promo_tokopedia',    
    'bundle',    
    'fft_coef_3_imag',
    'fft_coef_1_imag',    
    'abs_energy',
    'longest_strike_below_mean',
    'absolute_sum_of_changes',    
    'competitor_observed_price',
    'competitor_max_promo_discount',    
    'product_group',    
    'media_contact_nb_units',
    'media_contact_spend_net',
    'fact_media_discovery_ads_item_sold',
    'fact_media_discovery_ads_gmv',
    'fact_media_discovery_Cost',
    'fact_media_keywords_ads_item_sold',
    'fact_media_keywords_ads_gmv',
    'fact_media_keywords_cost',
    'media_sdds_spend',    
    'covid_cases',
    'covid_cases_ma_lag14d',
    'covid_deaths',    
    'availability_to_purchase_APPstore',
    'availability_to_purchase_web',
    'out_of_stock_ratio_web',
    'out_of_stock_ratio_app',    
    'product_rating',
    'product_review_count',
    'review_ma_7d',    
    'banner_brand_count',
    'banner_share_media']    

    - category_baseline: 
        - product_baseline:
        - train/test split: select the 90% of data as train data based on the timeline, the newest data are used for testing
        - correlation analysis with sales: the top5 <sales_lag from 1 day to 4 day> + discount_rate + competitor_observed_price
        - data cleaning:
          - missing values:
          - numeric columns:
          - mean values filling for ['fft_coef_3_imag', 'fft_coef_1_imag', 'abs_energy','longest_strike_below_mean','absolute_sum_of_changes']
          - group-based backfill for rest numeric columns
          - group-based frontfill for 
          - dates:
          - regard it as a missing date if sales = 0
          - if it's missing date then all numeric_cols = 0, else keep original values
         - create new time features:
           - week,day,quarter,doy(day of year),year, 
           - get sin() and cos() of them
        - 
 

2. Deploy the model and make real predictions
3. Model testing  
4. UI creating 
4. Deployment 
