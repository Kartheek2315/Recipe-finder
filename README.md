# Recipe-finder
import csv
import random

def generate_recipe_finder_csv(filename="recipe_finder.csv", n_rows=1000):
    cuisines = ["Indian", "Italian", "Chinese", "Mexican",
                "American", "Thai", "Japanese", "French"]
    meal_types = ["Breakfast", "Lunch", "Dinner", "Snack", "Dessert"]
    difficulties = ["Easy", "Medium", "Hard"]

    ingredients_pool = [
        "chicken", "onion", "tomato", "garlic", "ginger", "green chili",
        "potato", "butter", "oil", "salt", "pepper", "turmeric", "cumin",
        "coriander", "garam masala", "rice", "pasta", "cheese", "milk",
        "cream", "egg", "flour", "sugar", "honey", "soy sauce", "vinegar",
        "lemon", "cilantro", "basil", "oregano", "chili powder", "spinach",
        "carrot", "peas", "paneer", "beef", "pork", "fish", "shrimp",
        "yogurt", "mustard", "ketchup", "mushroom", "bell pepper",
        "broccoli", "cauliflower", "cabbage", "bread", "noodles"
    ]

    fieldnames = [
        "recipe_id",
        "recipe_name",
        "cuisine",
        "meal_type",
        "difficulty",
        "cook_time_minutes",
        "num_ingredients",
        "ingredients",
        "calories"
    ]

    recipes = []

    for i in range(1, n_rows + 1):
        cuisine = random.choice(cuisines)
        meal_type = random.choice(meal_types)
        difficulty = random.choice(difficulties)
        cook_time = random.randint(10, 180)          # 10 to 180 minutes
        num_ingredients = random.randint(4, 12)      # 4 to 12 ingredients
        ingredients = random.sample(ingredients_pool, num_ingredients)
        calories = random.randint(100, 900)          # 100 to 900 kcal

        recipe = {
            "recipe_id": i,
            "recipe_name": f"Recipe {i}",
            "cuisine": cuisine,
            "meal_type": meal_type,
            "difficulty": difficulty,
            "cook_time_minutes": cook_time,
            "num_ingredients": num_ingredients,
            "ingredients": ", ".join(ingredients),
            "calories": calories
        }
        recipes.append(recipe)

    with open(filename, "w", newline="", encoding="utf-8") as f:
        writer = csv.DictWriter(f, fieldnames=fieldnames)
        writer.writeheader()
        writer.writerows(recipes)

if __name__ == "__main__":
    generate_recipe_finder_csv()
    print("recipe_finder.csv generated successfully with 1000 rows.")