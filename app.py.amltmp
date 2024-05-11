import streamlit as st
import openai

# Set up OpenAI client
def setup_openai_client():
    api_key = st.secrets["OPENAI_API_KEY"]
    client = openai.OpenAI(api_key=api_key)
    return client

# Function to ask GPT a question and get the response
def ask_gpt(prompt, client):
    """
    This function takes a prompt and returns the response from OpenAI's GPT model.
    """
    try:
        response = client.chat.completions.create(
            model="gpt-4",  # Replace with your desired GPT model
            messages=[{"role": "user", "content": prompt}]
        )
        return response.choices[0].message.content
    except Exception as e:
        return f"An error occurred: {e}"

# Main function to drive the app
def main():
    st.title("GPT Query Interface")
    client = setup_openai_client()
    user_prompt = st.text_input("Enter your prompt:")

    if user_prompt:
        answer = ask_gpt(user_prompt, client)
        st.text_area("Answer from GPT:", value=answer, height=300)

if __name__ == "__main__":
    main()
