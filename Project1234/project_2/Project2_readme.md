# Project 2 

Objective: Tasked with creating a regression model based on the Ames Housing Dataset. This model will predict the price of a house at sale.

## Problem Statement

1. Main issue we are facing is the vast amount of data columns
2. Model can only contain at most 30 columns, this includes get dummies feature columns
3. How do we data clean?
4. How we do select the data columns?

## Executive Summary

1. Data was imported with keep_default_na=False, meaning null values will be 'NA' string
2. This is useful for categorical columns that have an actual NA categorical value
3. Heatmaps and boxplots were used to identify variables with correlated to price and low multicollinearity.
4. Mapped ordinal categories to numbers to rank more clearly
5. Boxplots were used to analyze categorical columns. For example, overall condition stood out as rank 5 had highest median sale price instead of 9 where 9 is the highest rank.
6. Did interaction feature engineering 
7. Ordinal columns were turned into get dummy features.
8. Modeling was done with train test split, cross validation score, GridsearchCV to find best parameters, linear regression
9. Regularization using ridge, lasso and elastic net were used.
10. Lasso was used to predict housing prices because it reduces coefficients to 0, bringing down number of variables to 28.
11. With Lasso, the score on unseen X_test_mc data is 0.85. 

## Outcome

Lasso modeling retained 28 features

building_age
condition_1_Feedr
condition_1_Norm
condition_1_PosA
condition_1_PosN
condition_1_RRAe
condition_1_RRAn
condition_1_RRNe
firenum_qual
foundation_CBlock
foundation_PConc
foundation_Slab
heating_qc
house_style_1Story
house_style_2.5Unf
house_style_SLvl
ms_subclass_160
ms_subclass_190
ms_subclass_20
ms_subclass_30
ms_subclass_40
ms_subclass_50
ms_subclass_60
ms_subclass_70
ms_subclass_75
ms_subclass_90
totrms_abvgrd
year_remod/add

What factors influence the house price:

The kind of infrastructure nearby the house such as railroads and parks. This is undestandable as people would like recreational facilties near their house or prefer to be further away from noisy vehicles like trains

The style of the house. Different people have different preferences in the shape and stories of their houses

The kind of dwelling is important as people will be inside their houses and the internal features such as attics matter.

The foundation of the house such as brick and wood.

The number of fireplaces and quality of it, probably due to fact that Iowa experiences winters in freezing temperatures

The rooms that are above graded level, this is probably because occupants will spend most of their time there

The quality of the basement


## Data Dictionary

|Column|Type|Description| 
|:-:|:-:|:-|
|id|int|**ID**|
|pid|int|**Property ID Number**|
|ms_subclass|object|**The building class** <br> 20 : 1-STORY 1946 & NEWER ALL STYLES <br>30 : 1-STORY 1945 & OLDER<br>40 : 1-STORY W/FINISHED ATTIC ALL AGES<br>45 : 1-1/2 STORY - UNFINISHED ALL AGES<br>50 : 1-1/2 STORY FINISHED ALL AGES<br>60 : 2-STORY 1946 & NEWER<br>70 : 2-STORY 1945 & OLDER<br>75 : 2-1/2 STORY ALL AGES<br>80 : SPLIT OR MULTI-LEVEL<br>85 : SPLIT FOYER<br>90 : DUPLEX - ALL STYLES AND AGES<br>120 : 1-STORY PUD (Planned Unit Development) - 1946 & NEWER<br>150 : 1-1/2 STORY PUD - ALL AGES<br>160 : 2-STORY PUD - 1946 & NEWER<br>180 : PUD - MULTILEVEL - INCL SPLIT LEV/FOYER<br>190 : 2 FAMILY CONVERSION - ALL STYLES AND AGES|
|ms_zoning|object|**Identifies the general zoning classification of the sale.**<br>A : Agriculture<br>C : Commercial<br>FV : Floating Village Residential<br>I : Industrial<br>RH : Residential High Density<br>RL : Residential Low Density<br>RP : Residential Low Density Park<br>RM : Residential Medium Density|
|lot_frontage|float|**Linear feet of street connected to property**|
|lot_area|float|**Lot size in square feet**|
|street|object|**Type of road access to property**<br>Grvl : Gravel<br>Pave : Paved|
|alley|object|**Type of alley access to property**<br>Grvl : Gravel<br>Pave : Paved<br>NA : No alley access|
|lot_shape|int|**LotShape: General shape of property**<br>Reg : Regular<br>IR1 : Slightly irregular<br>IR2 : Moderately Irregular<br>IR3 : Irregular|
|land_contour|object|**LandContour: Flatness of the property**<br>Lvl : Near Flat/Level<br>Bnk : Banked - Quick and significant rise from street grade to building<br>HLS : Hillside - Significant slope from side to side<br>Low Depression|
|utilities|int|**Type of utilities available**<br>AllPub : All public Utilities (E,G,W,& S)<br>NoSewr : Electricity, Gas, and Water (Septic Tank)<br>NoSeWa : Electricity and Gas Only<br>ELO : Electricity only|
|lot_config|object|**Lot configuration**<br>Inside : Inside lot<br>Corner : Corner lot<br>CulDSac : Cul-de-sac<br>FR2 : Frontage on 2 sides of property<br>FR3 : Frontage on 3 sides of property|
|land_slope|int|**Slope of property**<br>Gtl : Gentle slope<br>Mod : Moderate Slope<br>Sev : Severe Slope|
|neighborhood|object|**Physical locations within Ames city limits**<br>Blmngtn : Bloomington Heights<br>Blueste : Bluestem<br>BrDale : Briardale<br>BrkSide : Brookside<br>ClearCr : Clear Creek<br>CollgCr : College Creek<br>Crawfor : Crawford<br>Edwards : Edwards<br>Gilbert : Gilbert<br>IDOTRR : Iowa DOT and Rail Road<br>Meadow : Meadow Village<br>Mitchel : Mitchell<br>Names : North Ames<br>NoRidge : Northridge<br>NPkVill : Northpark Villa<br>NridgHt : Northridge Heights<br>NWAmes : Northwest Ames<br>OldTown : Old Town<br>SWISU : South & West of Iowa State University<br>Sawyer : Sawyer<br>SawyerW : Sawyer West<br>Somerst : Somerset<br>StoneBr : Stone Brook<br>Timber : Timberland<br>Veenker : Veenker|
|condition_1|object|**Proximity to main road or railroad**<br>Artery : Adjacent to arterial street<br>Feedr : Adjacent to feeder street<br>Norm : Normal<br>RRNn : Within 200' of North-South Railroad<br>RRAn : Adjacent to North-South Railroad<br>PosN : Near positive off-site feature--park, greenbelt, etc.<br>PosA : Adjacent to postive off-site feature<br>RRNe : Within 200' of East-West Railroad<br>RRAe : Adjacent to East-West Railroad|
|condition_2|object|**Proximity to main road or railroad (if a second is present)**<br>Artery : Adjacent to arterial street<br>Feedr : Adjacent to feeder street<br>Norm : Normal<br>RRNn : Within 200' of North-South Railroad<br>RRAn : Adjacent to North-South Railroad<br>PosN : Near positive off-site feature--park, greenbelt, etc.<br>PosA : Adjacent to postive off-site feature<br>RRNe : Within 200' of East-West Railroad<br>RRAe : Adjacent to East-West Railroad|
|bldg_type|object|**Type of dwelling**<br>1Fam : Single-family Detached<br>2FmCon : Two-family Conversion; originally built as one-family dwelling<br>Duplx : Duplex<br>TwnhsE : Townhouse End Unit<br>TwnhsI : Townhouse Inside Unit|
|house_style|object|**Style of dwelling**<br>1Story : One story<br>1.5Fin : One and one-half story: 2nd level finished<br>1.5Unf : One and one-half story: 2nd level unfinished<br>2Story : Two story<br>2.5Fin : Two and one-half story: 2nd level finished<br>2.5Unf : Two and one-half story: 2nd level unfinished<br>SFoyer : Split Foyer<br>SLvl : Split Level|
|overall_qual|int|**Overall material and finish quality**<br>10 : Very Excellent<br>9 : Excellent<br>8 : Very Good<br>7 : Good<br>6 : Above Average<br>5 : Average<br>4 : Below Average<br>3 : Fair<br>2 : Poor<br>1 : Very Poor|
|overall_cond|int|**Overall condition rating**<br>10 : Very Excellent<br>9 : Excellent<br>8 : Very Good<br>7 : Good<br>6 : Above Average<br>5 : Average<br>4 : Below Average<br>3 : Fair<br>2 : Poor<br>1 : Very Poor|
|year_built|int|**Original construction date**|
|year_remod/add|int|**Remodel date (same as construction date if no remodeling or additions)**|
|roof_style|object|**Type of roof**<br>Flat : Flat<br>Gable : Gable<br>Gambrel : Gabrel (Barn)<br>Hip : Hip<br>Mansard : Mansard<br>Shed : Shed|
|roof_matl|object|**Roof material**<br>ClyTile : Clay or Tile<br>CompShg : Standard (Composite) Shingle<br>Membran : Membrane<br>Metal : Metal<br>Roll : Roll<br>Tar&Grv : Gravel & Tar<br>WdShake : Wood Shakes<br>WdShngl : Wood Shingles|
|exterior_1st|object|**Exterior covering on house**<br>AsbShng : Asbestos Shingles<br>AsphShn : Asphalt Shingles<br>BrkComm : Brick Common<br>BrkFace : Brick Face<br>CBlock : Cinder Block<br>CemntBd : Cement Board<br>HdBoard : Hard Board<br>ImStucc : Imitation Stucco<br>MetalSd : Metal Siding<br>Other : Other<br>Plywood : Plywood<br>PreCast : PreCast<br>Stone : Stone<br>Stucco : Stucco<br>VinylSd : Vinyl Siding<br>Wd Sdng : Wood Siding<br>WdShing : Wood Shingles|
|exterior_2nd|object|**Exterior covering on house (if more than one material)**<br>AsbShng : Asbestos Shingles<br>AsphShn : Asphalt Shingles<br>BrkComm : Brick Common<br>BrkFace : Brick Face<br>CBlock : Cinder Block<br>CemntBd : Cement Board<br>HdBoard : Hard Board<br>ImStucc : Imitation Stucco<br>MetalSd : Metal Siding<br>Other : Other<br>Plywood : Plywood<br>PreCast : PreCast<br>Stone : Stone<br>Stucco : Stucco<br>VinylSd : Vinyl Siding<br>Wd Sdng : Wood Siding<br>WdShing : Wood Shingles|
|mas_vnr_type|object|**Masonry veneer type**<br>BrkCmn : Brick Common<br>BrkFace : Brick Face<br>Block : Cinder Block<br>None : None<br>Stone : Stone|
|mas_vnr_area|float|**Masonry veneer area in square feet**|
|exter_qual|object|**Exterior material quality**<br>Ex : Excellent<br>Gd : Good<br>TA : Average/Typical<br>Fa : Fair<br>Po : Poor|
|exter_cond|int|**Present condition of the material on the exterior**<br>Ex : Excellent<br>Gd : Good<br>TA : Average/Typical<br>Fa : Fair<br>Po : Poor|
|foundation|object|**Type of foundation**<br>BrkTil : Brick & Tile<br>CBlock : Cinder Block<br>PConc : Poured Contrete<br>Slab : Slab<br>Stone : Stone<br>Wood : Wood|
|bsmt_qual|int|**Height of the basement**<br>Ex : Excellent (100+ inches)<br>Gd : Good (90-99 inches)<br>TA : Typical (80-89 inches)<br>Fa : Fair (70-79 inches)<br>Po : Poor (<70 inches)<br>NA : No Basement|
|bsmt_cond|int|General condition of the basement<br>Ex : Excellent<br>Gd : Good<br>TA : Typical - slight dampness allowed<br>Fa : Fair - dampness or some cracking or settling<br>Po : Poor - Severe cracking, settling, or wetness<br>NA : No Basement|
|bsmt_exposure|int|**Walkout or garden level basement walls**<br>Gd : Good Exposure<br>Av : Average Exposure (split levels or foyers typically score average or above)<br>Mn : Mimimum Exposure<br>No : No Exposure<br>NA : No Basement|
|bsmtfin_type_1|int|**Quality of basement finished area**<br>GLQ : Good Living Quarters<br>ALQ : Average Living Quarters<br>BLQ : Below Average Living Quarters<br>Rec : Average Rec Room<br>LwQ : Low Quality<br>Unf : Unfinshed<br>NA : No Basement|
|bsmtfin_sf_1|float|**Type 1 finished square feet**|
|bsmtfin_type_2|object|**Quality of second finished area (if present)**<br>GLQ : Good Living Quarters<br>ALQ : Average Living Quarters<br>BLQ : Below Average Living Quarters<br>Rec : Average Rec Room<br>LwQ : Low Quality<br>Unf : Unfinshed<br>NA : No Basement|
|bsmtfin_sf_2|float|**Type 2 finished square feet**|
|bsmt_unf_sf|float|**Unfinished square feet of basement area**|
|total_bsmt_sf|float|**Total square feet of basement area**|
|heating|object|**Type of heating**<br>Floor : Floor Furnace<br>GasA : Gas forced warm air furnace<br>GasW : Gas hot water or steam heat<br>Grav : Gravity furnace<br>OthW : Hot water or steam heat other than gas<br>Wall : Wall furnace|
|heating_qc|int|**Heating quality and condition**<br>Ex : Excellent<br>Gd : Good<br>TA : Average/Typical<br>Fa : Fair<br>Po : Poor|
|central_air|object|**Central air conditioning**<br>N : No<br>Y : Yes|
|electrical|int|**Electrical system**<br>SBrkr : Standard Circuit Breakers & Romex<br>FuseA : Fuse Box over 60 AMP and all Romex wiring (Average)<br>FuseF : 60 AMP Fuse Box and mostly Romex wiring (Fair)<br>FuseP : 60 AMP Fuse Box and mostly knob & tube wiring (poor)<br>Mix : Mixed|
|1st_flr_sf|float|**First Floor square feet**|
|2nd_flr_sf|float|**Second floor square feet**|
|low_qual_fin_sf|int|**Low quality finished square feet (all floors)**|
|gr_liv_area|int|**Above grade (ground) living area square feet**|
|bsmt_full_bath|float|**Basement full bathrooms**|
|bsmt_half_bath|float|**Basement half bathrooms**|
|full_bath|int|**Full bathrooms above grade**|
|half_bath|int|**Half baths above grade**|
|bedroom_abvgr|int|**Number of bedrooms above basement level**|
|kitchen_abvgr|int|**Number of kitchens**|
|kitchen_qual|int|**Kitchen quality**<br>Ex : Excellent<br>Gd : Good<br>TA : Typical/Average<br>Fa : Fair<br>Po : Poor|
|totrms_abvgrd|int|**Total rooms above grade (does not include bathrooms)**|
|functional|int|**Home functionality rating**<br>Typ : Typical Functionality<br>Min1 : Minor Deductions 1<br>Min2 : Minor Deductions 2<br>Mod : Moderate Deductions<br>Maj1 : Major Deductions 1<br>Maj2 : Major Deductions 2<br>Sev : Severely Damaged<br>Sal : Salvage only|
|fireplaces|int|**Number of fireplaces**|
|fireplace_qu|int|**Fireplace quality**<br>Ex : Excellent - Exceptional Masonry Fireplace<br>Gd : Good - Masonry Fireplace in main level<br>TA : Average - Prefabricated Fireplace in main living area or Masonry Fireplace in basement<br>Fa : Fair - Prefabricated Fireplace in basement<br>Po : Poor - Ben Franklin Stove<br>NA : No Fireplace|
|garage_type|object|**Garage location**<br>2Types : More than one type of garage<br>Attchd : Attached to home<br>Basment : Basement Garage<br>BuiltIn : Built-In (Garage part of house - typically has room above garage)<br>CarPort : Car Port<br>Detchd : Detached from home<br>NA : No Garage|
|garage_yr_blt|int|**Year garage was built**|
|garage_finish|object|**Interior finish of the garage**<br>Fin : Finished<br>RFn : Rough Finished<br>Unf : Unfinished<br>NA : No Garage|
|garage_cars|in|**Size of garage in car capacity**|
|garage_area|float|**Size of garage in square feet**|
|garage_qual|in|**Garage quality**<br>Ex : Excellent<br>Gd : Good<br>TA : Typical/Average<br>Fa : Fair<br>Po : Poor<br>NA : No Garage|
|garage_cond|int|**Garage condition**<br>Ex : Excellent<br>Gd : Good<br>TA : Typical/Average<br>Fa : Fair<br>Po : Poor<br>NA : No Garage|
|paved_drive|int|**Paved driveway**<br>Y : Paved<br>P : Partial Pavement<br>N : Dirt/Gravel|
|wood_deck_sf|float|**Wood deck area in square feet**|
|open_porch_sf|float|**Open porch area in square feet**|
|enclosed_porch|float|**Enclosed porch area in square feet**|
|3ssn_porch|float|**Three season porch area in square feet**|
|screen_porch|float|**Screen porch area in square feet**|
|pool_area|float|**Pool area in square feet**|
|pool_qc|int|**Pool quality**<br>Ex : Excellent<br>Gd : Good<br>TA : Average/Typical<br>Fa : Fair<br>NA : No Pool|
|fence|int|**Fence quality**<br>GdPrv : Good Privacy<br>MnPrv : Minimum Privacy<br>GdWo : Good Wood<br>MnWw : Minimum Wood/Wire<br>NA : No Fence|
|misc_feature|object|**Miscellaneous feature not covered in other categories**<br>Elev : Elevator<br>Gar2 : 2nd Garage (if not described in garage section)<br>Othr : Other<br>Shed : Shed (over 100 SF)<br>TenC : Tennis Court<br>NA : None|
|misc_val|float|**$Value of miscellaneous feature**|
|mo_sold|int|**Month Sold**|
|yr_sold|int|**Year Sold**|
|sale_type|object|**Type of sale**<br>WD : Warranty Deed - Conventional<br>CWD : Warranty Deed - Cash<br>VWD : Warranty Deed - VA Loan<br>New : Home just constructed and sold<br>COD : Court Officer Deed/Estate<br>Con : Contract 15\% Down payment regular terms<br>ConLw : Contract Low Down payment and low interest<br>ConLI : Contract Low Interest<br>ConLD : Contract Low Down<br>Oth : Other|
|saleprice|float|**Property's sale price in dollars**|

