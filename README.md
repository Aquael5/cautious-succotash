#succotash-cauteloso:
Sempre pesquisando, ouvindo pessoas, aprimorando constante. Suibi este código galera,via celular, não usei o Git via computador, tranquilo,depois resolvo os procedimentos cabíveis.
import requests

def get_exchange_rate(from_currency, to_currency):
  """Gets the exchange rate between two currencies.

  Args:
    from_currency: The currency to convert from.
    to_currency: The currency to convert to.

  Returns:
    The exchange rate between the two currencies.
  """

  url = "https://api.exchangeratesapi.io/latest"
  params = {
    "base": from_currency,
    "symbols": to_currency,
  }

  response = requests.get(url, params=params)
  response.raise_for_status()

  data = response.json()
  exchange_rate = data["rates"][to_currency]

  return exchange_rate

def main():
  """The main function.

  Prompts the user for the amount of money to convert and the two currencies.
  Converts the amount of money and prints the result.
  """

  amount = input("Enter the amount of money to convert: ")
  from_currency = input("Enter the currency to convert from: ")
  to_currency = input("Enter the currency to convert to: ")

  exchange_rate = get_exchange_rate(from_currency, to_currency)
  converted_amount = float(amount) * exchange_rate

  print(f"{amount} {from_currency} is equal to {converted_amount} {to_currency}")

if __name__ == "__main__":
  main()
