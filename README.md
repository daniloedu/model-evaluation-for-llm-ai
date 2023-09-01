## OpenAI Model Evaluation for Product and Category Extraction

### Overview

The purpose of this Jupyter notebook is to evaluate the performance of an OpenAI model in the context of customer service. Specifically, it gauges the model's ability to extract product and category details from various customer messages. The evaluation is based on a set of predetermined "ideal" answers, allowing us to compute a performance score for the model.

### Key Components

1. **Set Up**: The notebook starts by importing necessary libraries, setting up the path for helper utilities, and loading the OpenAI API key from the environment variables.
2. **Model Interaction Functions**: 
   - `get_completion_from_messages()`: Fetches completion suggestions from the OpenAI API.
   - `find_category_and_product_v1()` and `find_category_and_product_v2()`: These functions guide the model using few-shot prompts to extract product and category information from customer messages.
3. **Evaluation**: The notebook contains pre-defined customer messages and their ideal outputs in the `msg_ideal_pairs_set`. Using the model interaction functions, the responses from the model are compared with these ideal outputs to determine the accuracy.
4. **Scoring**: The function `eval_response_with_ideal()` is used to compare the model's outputs with the ideal answers and calculate a score based on correct matches.

### Utility Documents `utils.py` functions:
  - `get_products_and_category():` This function reads the JSON file containing product details and returns a dictionary of products categorized by their types.
  - `find_category_and_product_only(user_input, products_data):` Accepts user input and the product data, then identifies and extracts the categories and products    mentioned in the user input.
  - `generate_output_string(category_and_product_list):` Uses the identified categories and products to generate a formatted output string containing relevant product details.

### JSON products file data
The provided JSON file contains detailed information about various products. Here's a breakdown of its structure:

- **Product Identifier**: Each product is uniquely identified by its name.
- **Attributes**: Each product has multiple attributes associated with it:
   - `name`: Name of the product
   - `category`: Category to which the product belongs
   - `brand`: Brand name of the product
   - `model_number`: Model number of the product
   - `warranty`: Warranty period
   - `rating`: Rating out of 5
   - `features`: A list of features associated with the product
   - `description`: A brief description of the product
   - `price`: Price of the product

From a cursory analysis, the JSON primarily contains information about products. The products span various categories like "Computers and Laptops", "Smartphones and Accessories", "Televisions and Home Theater Systems", "Gaming Consoles and Accessories", "Audio Equipment", and "Cameras and Camcorders". 


### Usage

1. Ensure you have the helper functions and product data in the correct directory, as referenced in the notebook.
2. Run the notebook cells in sequence. The notebook will use the OpenAI API to process the customer messages and will then evaluate the model's output.
3. The final cell computes the overall performance score, indicating how well the model's responses align with the expected answers.

### Notes

- This notebook relies on helper functions, which are presumably defined in an external file named `utils.py`. It may be beneficial to familiarize oneself with the functions in this file for a deeper understanding.
- The notebook also reads product and category data from a JSON file, which is essential for the evaluation process. Ensure this data is available and correctly formatted.
- This is an evaluation notebook. It's crucial to note that the model's performance may vary depending on the intricacies of the prompts, the nature of the customer messages, and the quality of the "ideal" answers set.

