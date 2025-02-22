# Smart Product Search App

## Overview

The Smart Product Search App is a Streamlit application that helps users find products, compare prices, and get detailed information about shipping and refund policies. It leverages a local SQLite database for product information and the Ollama LLM for providing helpful suggestions when a product search yields no results.  It also features an AI assistant for suggestions and promo codes.

## Features

*   **Product Search:** Find products based on keywords and natural language queries.
*   **Intent Detection:** Automatically determines the user's intent (search, shipping, refund, compare, discount) to provide relevant information.
*   **Relevance Scoring:** Ranks search results based on the relevance of product names, descriptions, brands, and categories.
*   **Location-Based Shipping Information:** Provides estimated delivery dates and shipping costs based on the user's selected city (major cities, tier 2 cities, or other cities).
*   **Refund Policy Details:** Displays comprehensive refund policies, including return windows, conditions for full/partial refunds, and non-returnable items.
*   **Price Comparison:** Compares prices of the same product across different platforms (if available in the database).
*   **AI Assistant:** Uses the Ollama LLM to provide helpful suggestions and alternatives when a product is not found in the database.
*   **Promo Codes:** Allows users to apply promo codes for discounted prices.
*   **User-Friendly Interface:** Clean and intuitive Streamlit interface with rounded images, modern design, and easy-to-use input fields.

## Technologies Used

*   Python 3.7+
*   Streamlit
*   SQLite
*   Ollama 

## Setup and Installation

1.  **Clone the repository:**

    ```bash
    git clone <your_repository_url>
    cd <your_repository_directory>
    ```

2.  **Install dependencies:**

    ```bash
    pip install streamlit sqlite3 ollama
    ```

3.  **Download the ollama model:**

    ```bash
    ollama pull llama3.2
    ```

## Usage Examples

Here are some example queries you can try:

*   **Search for a product:**
    *   `"Where can I find a Rolex Submariner"`
    *   `"Find AirPods Pro"`
    *   `"Show me samsung galaxy s24"`
*   **Get shipping information:**
    *   `"When will my order of iPhone 15 Pro deliver if I order today?"`
    *   `"Deliver iPhone 15 Pro"`
    *   `"When will AirPods Pro arrive in Bangalore?"`
*   **Check refund policy:**
    *   `"Refund policy for Samsung watch"`
    *   `"What is the return policy for a Sony headphones?"`
*   **Compare prices:**
    *   `"Compare prices for Samsung watch"`
    *   `"Price comparison for iPhone 15 Pro"`
*   **Find discounts:**
    *   `"Show me discounts for Nike shoes"`
    *   `"Promo code for apple watch"`
