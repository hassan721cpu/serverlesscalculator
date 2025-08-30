def lambda_handler(event, context):
    # Get query parameters safely
    a = float(event['queryStringParameters'].get('a', 0))
    b = float(event['queryStringParameters'].get('b', 0))
    op = event['queryStringParameters'].get('op', 'add')

    # Perform calculation
    if op == 'add':
        result = a + b
    elif op == 'subtract':
        result = a - b
    elif op == 'multiply':
        result = a * b
    elif op == 'divide':
        result = a / b if b != 0 else 'Infinity'
    else:
        result = 'Invalid Operation'

    # Return JSON response
    return {
        'statusCode': 200,
        'headers': {'Content-Type': 'application/json'},
        'body': str(result)
    }

