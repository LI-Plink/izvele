import requests

def dabut_joku():
    try:
        tema = input("Ievadi joku tēmu \\: ")
        url = 'https://api.chucknorris.io/jokes/random'

        if tema:
            url += f'?category={tema}'
            response = requests.get(url)
            print("Joks:", response.json()['value'])
    except:
        print("Radās kļūda iegūstot joku.")

def dabut_laiku():
    try:
        city = input("Ievadi pilsētu: ")
        api_key = 'tavs_api_key'
        url = f"http://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}&units=metric&lang=lv"
        response = requests.get(url)
        data = response.json()
        print(f"Temperatūra:{data["main"]["temp"]}°C")
        print("Apraksts:", data["weather"][0]["description"])
    except:
        print("Radās kļūda iegūstot laikapstākļus.")
def fakts_par_kakiem():
    try:
        response = requests.get("https://catfact.ninja/fact")
        print("Fakts:", response.json()['fact'])
    except:
        print("Radās kļūda iegūstot faktu.")

while True:
    print("Izvēlne:")
    print("1 - Nejaušs joks")
    print("2 - Laikapstākļi")
    print("3 - Fakts par kaķiem")
    print("0 - Iziet")

    choice = input("Tava izvele:")
    if choice == '1':
         dabut_joku()
    elif choice == '2':
         dabut_laiku()
    elif choice == '3':
        fakts_par_kakiem()
    elif choice == '0':
        break
    else:
        print("Nederīga izvēle!")
    
