print("ROOM AVAILABILITY SYSTEM")

# Dictionary for storing usernames and passwords
credentials = {}
occupied_rooms = {}
rooms = ["PTC303", "PTC304"]

while True:
    choice = input("Do you want to Login or Signup? (type 'exit' to quit): ").lower()
    
    if choice == "signup":
        username = input("Create a username: ")
        if username in credentials:
            print("Username already taken.")
        else:
            password = input("Create a password: ")
            credentials[username] = password
            print("Account created! You can now log in.")
    
    elif choice == "login":
        username = input("Username: ")
        password = input("Password: ")
        
        if credentials.get(username) == password:
            role = input("Are you a Teacher or a Student? ").lower()
            
            if role == "teacher":
                print(f"Welcome, Teacher {username}")
                print(f"Available rooms: {rooms}")
                print("Occupied rooms:", occupied_rooms or "None")
                
                chosen_room = input("Choose a room: ")
                if chosen_room in rooms:
                    rooms.remove(chosen_room)
                    occupied_rooms[chosen_room] = username
                    print(f"Room {chosen_room} reserved by {username}.")
                else:
                    print("Invalid choice or room already occupied.")
            
            elif role == "student":
                print(f"Welcome, {username} (Student)")
                print(f"Available rooms: {rooms}")
                print("Occupied rooms:", occupied_rooms or "None")
            
            else:
                print("Invalid role.")
        else:
            print("Invalid username or password.")
    
    elif choice == "exit":
        break

    else:
        print("Invalid option. Please choose 'login' or 'signup'.")
    
    print("\n--- Next User ---\n")
