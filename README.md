# Visual-Food-nutrition-estimator-Indian-Cuisine-
This project is a deep learning–based system that estimates calories and macronutrients (protein, carbs, fat) from images of Indian food. It combines image classification using fastai with a curated nutrition database to provide practical dietary insights for wellness, fitness, and health tech applications.


🧼 Data Cleaning Strategy
To ensure high-quality inputs for training while preserving as much data as possible, a delayed-drop strategy was used. Instead of immediately removing rows with missing values, missing fields were evaluated only after relevant calculations were completed.

📋 Key Steps

1:Initial Dataset Inspection

The dataset included nutritional values per 100g and sometimes per serving. However, some rows were missing fields like unit_serving_energy_kcal or servings_unit, which were not always critical to model training.

2:Calculated Derived Features

The serving_size_g was estimated using:

serving_size_g = (unit_serving_energy_kcal / energy_kcal) * 100
This derived field allows comparison between standardized values (per 100g) and actual real-world serving estimates.

3:Deferred Row Dropping

Rows were not dropped immediately based on missing values in columns like unit_serving_energy_kcal or servings_unit. Instead, missing values were removed only after key features were calculated.

4:Dropped Based on Core Nutritional Fields Only

Final cleaning retained only rows with valid values in the most essential columns:

calories_kcal,
carbs_g,
protein_g,
fat_g,
sugar_g,
fibre_g,
sodium_mg,
serving_size_g

This led to a final dataset of 932 complete and clean rows, compared to 914 rows using the earlier drop-first approach.

5:Reset Index

After dropping missing rows, the DataFrame index was reset for consistency.

✅ Why This Strategy?

More data retained: We preserve valid rows that might have been prematurely dropped.

Better model training: More diverse and complete examples improve generalization.

Real-world focused: Prioritizes fields that impact calorie/macronutrient prediction — not just metadata.



