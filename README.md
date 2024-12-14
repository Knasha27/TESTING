# TESTINGdef validate_input(data):
    """
    Validates employee data.
    :param data: Dictionary containing employee data
    :return: True if valid, otherwise False with error messages
    """
    errors = []
    if not data.get('name'):
        errors.append("Name cannot be empty.")
    if not isinstance(data.get('ID'), int):
        errors.append("ID must be an integer.")
    if not isinstance(data.get('dependents'), int) or data['dependents'] < 0:
        errors.append("Dependents must be a non-negative integer.")
    if not isinstance(data.get('hours_worked'), (int, float)) or data['hours_worked'] < 0:
        errors.append("Hours worked must be a non-negative number.")
    
    if errors:
        return False, errors
    return True, None

def test_data_input():
    test_cases = [
        {'name': 'John Doe', 'ID': 1001, 'dependents': 2, 'hours_worked': 40},
        {'name': 'Jane Smith', 'ID': 1002, 'dependents': 1, 'hours_worked': 45},
        {'name': 'Alice Johnson', 'ID': 1003, 'dependents': 0, 'hours_worked': 38},
        {'name': 'Bob Brown', 'ID': 1004, 'dependents': 3, 'hours_worked': 36},
        {'name': 'Charlie Davis', 'ID': 1005, 'dependents': 4, 'hours_worked': 50},
        {'name': 'Diana Evans', 'ID': 1006, 'dependents': 2, 'hours_worked': 40},
        {'name': 'Eve Foster', 'ID': 1007, 'dependents': 1, 'hours_worked': 48},
        {'name': 'Frank Green', 'ID': 1008, 'dependents': 0, 'hours_worked': 30},
        {'name': 'Grace Hill', 'ID': 1009, 'dependents': 2, 'hours_worked': 42},
        {'name': 'Hank Irving', 'ID': 1010, 'dependents': 1, 'hours_worked': 35},
    ]
    for case in test_cases:
        print(f"Testing: {case}")
        is_valid, errors = validate_input(case)
        if is_valid:
            print("Valid input.")
        else:
            print("Invalid input:", errors)

test_data_input()
