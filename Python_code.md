class Station:
    def __init__(self, name, distance):
        self.name = name
        self.distance = distance  # distance from previous station (km)
        self.prev = None
        self.next = None


class TrainRoute:
    def __init__(self, route_name, circular=False):
        self.route_name = route_name
        self.head = None
        self.tail = None
        self.current = None
        self.circular = circular

    # Add station (DLL insertion)
    def add_station(self, name, distance):
        new_station = Station(name, distance)

        if not self.head:
            self.head = self.tail = self.current = new_station
        else:
            self.tail.next = new_station
            new_station.prev = self.tail
            self.tail = new_station

        # Circular route support
        if self.circular:
            self.tail.next = self.head
            self.head.prev = self.tail

        print(f"Station '{name}' added.")

    # Display full route
    def show_route(self):
        if not self.head:
            print("No stations available.")
            return

        print(f"\nRoute: {self.route_name}")
        temp = self.head
        visited = set()

        while temp and temp not in visited:
            visited.add(temp)
            marker = " [CURRENT]" if temp == self.current else ""
            print(f"{temp.name}{marker}", end=" ⇄ ")
            temp = temp.next

        print("END")

    # Move forward
    def move_forward(self):
        if self.current and self.current.next:
            self.current = self.current.next
            print(f"Arrived at {self.current.name}")
        else:
            print("Cannot move forward.")

    # Move backward
    def move_backward(self):
        if self.current and self.current.prev:
            self.current = self.current.prev
            print(f"Arrived at {self.current.name}")
        else:
            print("Cannot move backward.")

    # Show current station
    def current_station(self):
        if self.current:
            print(f"Current Station: {self.current.name}")
        else:
            print("No station selected.")

    # Calculate total distance
    def total_distance(self):
        if not self.head:
            return

        total = 0
        temp = self.head
        visited = set()

        while temp and temp not in visited:
            visited.add(temp)
            total += temp.distance
            temp = temp.next

        print(f"Total Route Distance: {total} km")


# ---------------- MENU ----------------
if __name__ == "__main__":

    print("Create Route Type:")
    print("1. Normal Route")
    print("2. Circular Metro Route")

    choice = input("Choose: ")
    circular = True if choice == "2" else False

    route = TrainRoute("City Line", circular)

    while True:
        print("\n====== Advanced Train Route Planner ======")
        print("1. Add Station")
        print("2. Show Route")
        print("3. Current Station")
        print("4. Move Forward")
        print("5. Move Backward")
        print("6. Show Total Distance")
        print("7. Exit")

        option = input("Choose option: ")

        if option == "1":
            name = input("Enter station name: ")
            dist = float(input("Distance from previous station (km): "))
            route.add_station(name, dist)

        elif option == "2":
            route.show_route()

        elif option == "3":
            route.current_station()

        elif option == "4":
            route.move_forward()

        elif option == "5":
            route.move_backward()

        elif option == "6":
            route.total_distance()

        elif option == "7":
            print("Exiting Planner...")
            break

        else:
            print("Invalid choice.")
