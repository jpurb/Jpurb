```python
def read_route_data(file_name):
    try:
        with open(file_name, 'r') as file:
            routes = []
            route_set = set()  # To check for duplicate routes
            for line in file:
                line = line.strip()
                if not line:
                    continue  # Skip empty lines
                parts = line.split(',')
                if len(parts) != 3:
                    raise ValueError("Invalid data format in routes.txt")
                route_number, n_happy, n_unhappy = parts
                route_number = int(route_number)
                n_happy = int(n_happy)
                n_unhappy = int(n_unhappy)
                if route_number in route_set:
                    raise ValueError("Duplicate route in routes.txt")
                route_set.add(route_number)
                routes.append({
                    'route_number': route_number,
                    'n_happy': n_happy,
                    'n_unhappy': n_unhappy,
                    'happy_ratio': n_happy / max(n_unhappy, 1)  # Avoid division by zero
                })
        return routes
    except FileNotFoundError:
        raise FileNotFoundError("routes.txt not found")
    except Exception as e:
        raise Exception(f"Error reading data from routes.txt: {str(e)}")

def sort_route_data(routes):
    return sorted(routes, key=lambda x: (x['happy_ratio'], x['route_number']))

def main():
    try:
        file_name = "routes.txt"
        routes = read_route_data(file_name)
        n = input("How many routes can have an extra bus? ")
        while not n.isdigit() or int(n) <= 0 or int(n) > len(routes):
            print("Invalid value. Please enter a non-negative integer between 1 and", len(routes))
            n = input("How many routes can have an extra bus? ")
        n = int(n)
        sorted_routes = sort_route_data(routes)
        print("You should add busses for the following routes:")
        for i in range(n):
            print(sorted_routes[i]['route_number'])
    except Exception as e:
        print(e)

if __name__ == "__main__":
    main()







```

    How many routes can have an extra bus? 3
    You should add busses for the following routes:
    123
    567
    459
    
