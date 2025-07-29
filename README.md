def get_user_details():
print("--*--*--*--*--*--*--*--*--*--*--*--*--*--*--")
print("\n Welcome to the Personal Assistant!\n")
print("-*--*--*--*--*--*--*--*--*--*--*--*--*--*--")
print("\nLet's get to know you!\n")
name = input("What's your name?") .strip().title()
age = input("How old are you? ").strip() color = input("What's your favorite color? ").strip().lower()
city = input("Which city do you live in? ").strip().title()
shs = input("Which SHS did you attend? ").strip().title()
team = input("What's your favorite soccer team? ").strip().title()
return {
        "name": name,
        "age": age,
        "color": color,
        "city": city,
        "shs": shs,
        "team": team
    }

def generate_summary(user):
    summary = (
        f"Hello {user['name']}! You are {user['age']} years old, You love the color {user['color']}, "
        f"and you're a proud old student of {user['shs']}.\n"
        f"You support {user['team']} and life must be awesome in {user['city']}!"
    )
    return summary

def display_summary(user):
    print("\n Here's your fun summary!\n")
    print(generate_summary(user))

def save_to_file(user, rating):
    filename = f"{user['name']}.txt"
    summary_text = generate_summary(user)
    full_text = (
        " Personal Summary \n\n"
        f"{summary_text}\n\n"
        f"User Rating: {rating}/5 stars\n"
    )
    try:
        with open(filename, "w") as file:
            file.write(full_text)
        print(f"\n Summary saved to {filename}!\n")
    except Exception as e:
        print(f" Error saving file: {e}")

def main():
    while True:
        user = get_user_details()
        display_summary(user)
save = input("Would you like to save this summary to a .txt file? (yes/no): ").strip().lower()
        if save in ['yes', 'y']:
            while True:
                try:
                    rating = int(input("How would you rate this assistant? (1 to 5 stars): "))
                    if 1 <= rating <= 5:
                        break
                    else:
                        print("Please enter a number between 1 and 5.")
                except ValueError:
                    print("Please enter a valid number.")
            save_to_file(user, rating)
restart = input("Would you like to restart and enter another  info? (yes/no): ").strip().lower()
        if restart not in ['yes', 'y']:
            print("\n Thanks for using the assistant! Goodbye.\n")
            break

if __name__ == "__main__":
    main()
