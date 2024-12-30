import requests

def hava_durumu_cek(sehir, api_anahtari):

    url = f"http://api.openweathermap.org/data/2.5/weather?q={sehir}&appid={api_anahtari}&units=metric&lang=tr"

    response = requests.get(url)

    if response.status_code == 200:
        data = response.json()

        sehir_adi = data["name"]
        hava_durumu = data["weather"][0]["description"]
        sicaklik = data["main"]["temp"]

        print(f"{sehir_adi} şehrinde hava durmu : {hava_durumu}")
        print(f"Sıcaklık : {sicaklik} °c")

    else:
        print("Hava durumu bilgisi alırken hata oluştu. Lütfen geçerli bir şehir giriniz")

def hava_durumu():

    api_anahatri = "7d7afaeee37d3a865ca40813483bbe43"

    print("Hava durumu sorgulamak istediğiniz şehri giriniz:")
    sehir = input("Sehir giriniz: ")

    hava_durumu_cek(sehir, api_anahatri)

hava_durumu()






