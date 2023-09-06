```python
def get_positive_integer(prompt):
    while True:
        try:
            value = int(input(prompt))
            if value <= 0:
                raise ValueError
            return value
        except ValueError:
            print("Invalid input. Please enter a positive integer.")

def get_non_negative_integer(prompt):
    while True:
        try:
            value = int(input(prompt))
            if value < 0:
                raise ValueError
            return value
        except ValueError:
            print("Invalid input. Please enter a non-negative integer.")

def main():
    while True:
        print("Welcome to the Codetown Bus Passenger Tracker!")
        route_number = get_positive_integer("Please enter the route number: ")
        num_stops = get_positive_integer("Please enter the number of stops on this route: ")
        
        if num_stops < 3:
            print("Invalid number of stops. There must be at least three stops on the route.")
            continue

        passengers = get_positive_integer("How many passengers were waiting for the bus at stop #1? ")
        total_happy_customers = 0
        total_unhappy_customers = 0

        for stop in range(2, num_stops):
            passengers_off = get_non_negative_integer(f"How many passengers left the bus at stop #{stop}? ")
            passengers_waiting = get_non_negative_integer(f"How many passengers were waiting for the bus at stop #{stop}? ")
            passengers -= passengers_off

            if passengers < 0:
                print(f"Invalid number of passengers. Only {passengers_off + passengers} passengers were on the bus.")
                continue

            passengers += passengers_waiting
            unhappy_customers = max(0, passengers - 35)
            total_unhappy_customers += unhappy_customers
            total_happy_customers += passengers - unhappy_customers

        last_stop_passengers = get_non_negative_integer("How many passengers left the bus at the last stop? ")
        if last_stop_passengers != passengers:
            print(f"This is the last stop. There should be {passengers} passengers leaving.")
            continue

        print(f"Route number: {route_number}")
        print(f"Happy customers: {total_happy_customers}")
        print(f"Unhappy customers: {total_unhappy_customers}")
        
        if total_unhappy_customers == 0:
            ratio = 0.00
        else:
            ratio = round(total_happy_customers / total_unhappy_customers, 2)
        print(f"Ratio of happy to unhappy customers: {ratio}")

        another_route = input("Do you want to enter data for another route? (yes/no): ").lower()
        if another_route != 'yes':
            break

if __name__ == "__main__":
    main()







```

    Welcome to the Codetown Bus Passenger Tracker!
    Please enter the route number: 128
    Please enter the number of stops on this route: 3
    How many passengers were waiting for the bus at stop #1? 20
    How many passengers left the bus at stop #2? 12
    How many passengers were waiting for the bus at stop #2? 15
    How many passengers left the bus at the last stop? 10
    This is the last stop. There should be 23 passengers leaving.
    Welcome to the Codetown Bus Passenger Tracker!
    Please enter the route number: 125
    Please enter the number of stops on this route: 5
    How many passengers were waiting for the bus at stop #1? 12
    How many passengers left the bus at stop #2? 5
    How many passengers were waiting for the bus at stop #2? 8
    How many passengers left the bus at stop #3? 6
    How many passengers were waiting for the bus at stop #3? 15
    How many passengers left the bus at stop #4? 7
    How many passengers were waiting for the bus at stop #4? 12
    How many passengers left the bus at the last stop? 5
    This is the last stop. There should be 29 passengers leaving.
    Welcome to the Codetown Bus Passenger Tracker!
    Please enter the route number: 120
    Please enter the number of stops on this route: 5
    How many passengers were waiting for the bus at stop #1? 20
    How many passengers left the bus at stop #2? 11
    How many passengers were waiting for the bus at stop #2? 21
    How many passengers left the bus at stop #3? 15
    How many passengers were waiting for the bus at stop #3? 9
    How many passengers left the bus at stop #4? 6
    How many passengers were waiting for the bus at stop #4? 10
    How many passengers left the bus at the last stop? 6
    This is the last stop. There should be 28 passengers leaving.
    Welcome to the Codetown Bus Passenger Tracker!
    Please enter the route number: 121
    Please enter the number of stops on this route: 10
    How many passengers were waiting for the bus at stop #1? 5
    How many passengers left the bus at stop #2? 11
    How many passengers were waiting for the bus at stop #2? 9
    Invalid number of passengers. Only 5 passengers were on the bus.
    How many passengers left the bus at stop #3? 15
    How many passengers were waiting for the bus at stop #3? 10
    Invalid number of passengers. Only -6 passengers were on the bus.
    How many passengers left the bus at stop #4? 16
    How many passengers were waiting for the bus at stop #4? 11
    Invalid number of passengers. Only -21 passengers were on the bus.
    How many passengers left the bus at stop #5? 9
    How many passengers were waiting for the bus at stop #5? 4
    Invalid number of passengers. Only -37 passengers were on the bus.
    How many passengers left the bus at stop #6? 20
    How many passengers were waiting for the bus at stop #6? 21
    Invalid number of passengers. Only -46 passengers were on the bus.
    How many passengers left the bus at stop #7? 9
    How many passengers were waiting for the bus at stop #7? 13
    Invalid number of passengers. Only -66 passengers were on the bus.
    How many passengers left the bus at stop #8? 7
    How many passengers were waiting for the bus at stop #8? 19
    Invalid number of passengers. Only -75 passengers were on the bus.
    How many passengers left the bus at stop #9? 7
    How many passengers were waiting for the bus at stop #9? 19
    Invalid number of passengers. Only -82 passengers were on the bus.
    How many passengers left the bus at the last stop? 4
    This is the last stop. There should be -89 passengers leaving.
    Welcome to the Codetown Bus Passenger Tracker!
    Please enter the route number: 226
    Please enter the number of stops on this route: 6
    How many passengers were waiting for the bus at stop #1? 20
    How many passengers left the bus at stop #2? 9
    How many passengers were waiting for the bus at stop #2? 15
    How many passengers left the bus at stop #3? 9
    How many passengers were waiting for the bus at stop #3? 16
    How many passengers left the bus at stop #4? 9
    How many passengers were waiting for the bus at stop #4? 17
    How many passengers left the bus at stop #5? 15
    How many passengers were waiting for the bus at stop #5? 13
    How many passengers left the bus at the last stop? 10
    This is the last stop. There should be 39 passengers leaving.
    Welcome to the Codetown Bus Passenger Tracker!
    Please enter the route number: 7
    Please enter the number of stops on this route: 19
    How many passengers were waiting for the bus at stop #1? 15
    How many passengers left the bus at stop #2? 20
    How many passengers were waiting for the bus at stop #2? 13
    Invalid number of passengers. Only 15 passengers were on the bus.
    How many passengers left the bus at stop #3? 19
    How many passengers were waiting for the bus at stop #3? 15
    Invalid number of passengers. Only -5 passengers were on the bus.
    How many passengers left the bus at stop #4? 16
    How many passengers were waiting for the bus at stop #4? 3
    Invalid number of passengers. Only -24 passengers were on the bus.
    How many passengers left the bus at stop #5? 10
    How many passengers were waiting for the bus at stop #5? 5
    Invalid number of passengers. Only -40 passengers were on the bus.
    How many passengers left the bus at stop #6? 18
    How many passengers were waiting for the bus at stop #6? 10
    Invalid number of passengers. Only -50 passengers were on the bus.
    How many passengers left the bus at stop #7? 12
    How many passengers were waiting for the bus at stop #7? 10
    Invalid number of passengers. Only -68 passengers were on the bus.
    How many passengers left the bus at stop #8? 4
    How many passengers were waiting for the bus at stop #8? 19
    Invalid number of passengers. Only -80 passengers were on the bus.
    How many passengers left the bus at stop #9? 5
    How many passengers were waiting for the bus at stop #9? 23
    Invalid number of passengers. Only -84 passengers were on the bus.
    How many passengers left the bus at stop #10? 4
    How many passengers were waiting for the bus at stop #10? 12
    Invalid number of passengers. Only -89 passengers were on the bus.
    How many passengers left the bus at stop #11? 1
    How many passengers were waiting for the bus at stop #11? 10
    Invalid number of passengers. Only -93 passengers were on the bus.
    How many passengers left the bus at stop #12? 20
    How many passengers were waiting for the bus at stop #12? 20
    Invalid number of passengers. Only -94 passengers were on the bus.
    How many passengers left the bus at stop #13? 11
    How many passengers were waiting for the bus at stop #13? 10
    Invalid number of passengers. Only -114 passengers were on the bus.
    How many passengers left the bus at stop #14? 20
    How many passengers were waiting for the bus at stop #14? 1
    Invalid number of passengers. Only -125 passengers were on the bus.
    How many passengers left the bus at stop #15? 10
    How many passengers were waiting for the bus at stop #15? 2
    Invalid number of passengers. Only -145 passengers were on the bus.
    


```python

```
