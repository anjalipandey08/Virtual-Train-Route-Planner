class StationNode:
    def __init__(self, name):
        self.name = name
        self.prev = None
        self.next = None

class TrainRouteDLL:
    def __init__(self):
        self.head = None
        self.tail = None
        self.current = None

    def add_station(self, name):
        new_station = StationNode(name)
        if not self.head:
            self.head = self.tail = new_station
            self.current = new_station
        else:
            self.tail.next = new_station
            new_station.prev = self.tail
            self.tail = new_station
        print(f"Station '{name}' added to the route.")

    def show_route(self):
        if not self.head:
            print("No stations in the route.")
            return
        temp = self.head
        print("Train Route:", end=" ")
        while temp:
            if temp == self.current:
                print(f"[{temp.name}]", end=" ↔ ")
            else:
                print(temp.name, end=" ↔ ")
            temp = temp.next
        print("END")

    def show_current(self):
        if self.current:
            print(f"Currently at: {self.current.name}")
        else:
            print("No stations available.")

    def move_forward(self):
        if self.current and self.current.next:
            self.current = self.current.next
            print(f"Moved forward to {self.current.name}")
        else:
            print("End of the route reached.")

    def move_backward(self):
        if self.current and self.current.prev:
            self.current = self.current.prev
            print(f"Moved backward to {self.current.name}")
        else:
            print("Start of the route reached.")


# ----------- MENU BASED PROGRAM ------------
if __name__ == "__main__":
    route = TrainRouteDLL()

    while True:
        print("\n====== Virtual Train Route Planner (DLL) ======")
        print("1. Add Station")
        print("2. Show Route")
        print("3. Current Station")
        print("4. Move Forward")
        print("5. Move Backward")
        print("6. Exit")
        
        choice = input("Choose option: ")

        if choice == "1":
            name = input("Enter station name: ")
            route.add_station(name)

        elif choice == "2":
            route.show_route()

        elif choice == "3":
            route.show_current()

        elif choice == "4":
            route.move_forward()

        elif choice == "5":
            route.move_backward()

        elif choice == "6":
            print("Exiting... Goodbye!")
            break

        else:
            print("⚠️ Invalid choice! Please try again.")
