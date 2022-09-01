## Concepts and Definition
- Signature: Loreal paris, Lancome
- Brand/Axis: Loreal paris 
- Segment: 
- Subbrand:
- Franchise: revitalift
- promo_group:



### Set specific variables 
- current_category = 'skin'
- current_promogroup = "revitalift"
- current_customer = "Woolworths" 
- current_manufacturer = "lorealaust"

### Merge 3 categories of data 'df_category_data_combined'
- hair, skin, cosmetics

### All products in same category of same customer 'df_competitor_mapping'
df_full_data =  df_category_data_combined
df_category_data : select specific category
df_category_data_current_customer : select specific category and customer=

### Generate subbrands of competitors 
df_competitor_mapping: the *subbrands*(franchises of competitors) of competitors corresponding to every *promo_group*(different franchise under same brand)
competitor_subbrands: a list of the subbrands of current promo_group

### Aggregating data for modeling 
df_model_data_products: df_category_data_current_customer aggregate sales by product and date
df_model_data_promogroup: generate all dates 

### Generate the same info of *df_model_data_products* for other products of same subbrands and same segment
within *product_subset* func:
- lor_promogroup_products: the products under same promo_group and same manufacturer
- lor_promogroup_category: the categories under same promo_group and same manufacturer
- lor_promogroup_products_training: All products in customer with records over 30 weeks data
- lor_promogroup_brands: All brands/signatures that fall within the promogroup
- lor_promogroup_subbrands: All subbrands that fall within the promogroup
- current_promogroup_segments: All segments that fall within the promogroup
- lor_other_products_in_segments_subbrand:  Cannibalising - All products that are within the segment and subbrand but are not within the promogroup
- product_feature_dict:
to_merge_df: weekly sales of other products that are not in promo_group but under same segment and same subbrand
