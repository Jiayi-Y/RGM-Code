## Terms
- BAU: revised_RSP
- Direct discount: 
- ASP:actual selling price(售价）
- RSP:retail selling price(定价)
- Promotions: 1 product * 1 day = 1 promotion
------------------------------------------------
- brand:loreal paris skin
- category:skin/hair/cosmetics level
- sub_category:eye skincare/hair care/ 
- franchise:product_line eg revitalift of loreal paris

## Baseline building & Insights
### 01. Historical Baseline Construction & Incremental Measure
_Objective: Measure incremental GMV(the true impact of a promotion)_  

**Incremental GMV = GMV-incremental discount-pull forward effects&cannibalization**    

Steps:   
1. Seperate promo & non-promo events for all SKUs    
    **Promotion Sales**: Sales on days during which ASP is lower than RSP by 5% or more  
2. Reconstructing the historical baseline: use the most important features to predict sales          
    - sales scale<previous sales？>:measurements of sales performance of the product   
    - trend   
    - competitor prmotion   
    - pricing(BAU)
    
    **Pull forward effects**: consumers stop buying for a while after promo stock-up      
      - Compare gap between the total gross sales and total baseline during non-promotion periods    
      
    **Cannibalization effects**: promotional sales affect non-promo      
      - Calculate sales correlation to determine canni. granularity : chose category level since products within this level have highest correlation   
      - Build cannibalization baseline without promotion at category leve   
      - Calculate daily cannibalization: sum of lift up of products under one cate - sum of uplift at cate level      
        daily cannibalization rate : daily cannibalization/sum of uplift at ID(promo products of same cate) level   
     
     **other business metrics**
      - GMV uplift = GMV - Baseline
      - Incremental discounts: ASP vs. BAU
      - GMV/Promo Efficiency = Incre.GMV/ Incre.Discount
     
## Data cleaning & preparation
### Fundamental data sources:   
- Product data
  - SAP code: for each packaging variation of a prod
  - EAN code: SKU version
  - Shopee Product ID: single SKU and products in various bundles have different ID
  - Shopee Product Model ID:  a color/volume variation of a product under single SKU ID
- Promo calendar: signature level, daily    
- Flash Sales: With 2-2.5 years of flash sales data, we will take flash sales as a feature to predict sales   
- Other data sources:
  - Media data

## Measurement Approach
### Sept->Oct->Nov





