# Bulut-Bilisim-Odev2
Bulut Bilişim Dersi 2.Ödev Flask Uygulaması

Kullanılan Bulut Uygulaması : Google Cloud

# 1- Bir Sanal Makine Oluşturuldu. Bilgileri Aşağıdaki Gibidir.
<img width="588" height="219" alt="01" src="https://github.com/user-attachments/assets/66f68f30-e96e-4cc0-a6fc-7058b5717261" />

# 2- Web'de yayınlanmak üzere bir uygulama geliştirildi.

from flask import Flask, request, render_template_string

app = Flask(__name__)

# Basit bir HTML şablonu
HTML_SABLONU = """
<!DOCTYPE html>
<html>
<head><title>Bulut Mağazası</title></head>
<body>
    <h2>Ürünlerimiz</h2>
    <form method="POST">
        <select name="islem">
            <option value="1">Bilgisayar (69.999 TL)</option>
            <option value="2">Telefon (44.999 TL)</option>
            <option value="3">Konsol (29.999 TL)</option>
            <option value="4">Saat (9.999 TL)</option>
        </select>
        <input type="number" name="adet" placeholder="Adet giriniz" required>
        <button type="submit">Hesapla</button>
    </form>
    {% if sonuc %}
        <h3>{{ sonuc }}</h3>
    {% endif %}
</body>
</html>
"""

@app.route("/", methods=["GET", "POST"])
def index():
    sonuc = ""
    if request.method == "POST":
        islem = int(request.form.get("islem"))
        adet = int(request.form.get("adet"))
        fiyatlar = {1: 69999, 2: 44999, 3: 29999, 4: 9999}
        isimler = {1: "Bilgisayar", 2: "Telefon", 3: "Konsol", 4: "Saat"}
        
        tutar = fiyatlar[islem] * adet
        sonuc = f"Seçilen: {isimler[islem]} - Toplam Tutar: {tutar:,} TL"
    
    return render_template_string(HTML_SABLONU, sonuc=sonuc)

if __name__ == "__main__":
    # AWS EC2 üzerinde çalışması için 0.0.0.0 üzerinden 5000 portunda çalıştırıyoruz
    app.run(host="0.0.0.0", port=5000) 


# 3- Sanal Sunucu Başlatıldı
<img width="1260" height="162" alt="02" src="https://github.com/user-attachments/assets/be886fa6-4e7a-4d7c-90ef-19bb38c60e66" />

# 4- Güvenlik İzinleri Oluşturuldu.
<img width="264" height="652" alt="Ekran görüntüsü 2025-12-27 153547" src="https://github.com/user-attachments/assets/a3965e73-6a09-4d25-889c-d2e9b60cba37" />

# 5- Uygulama Çalıştırıldı
<img width="884" height="173" alt="Ekran görüntüsü 2025-12-27 151955" src="https://github.com/user-attachments/assets/97bc6a8b-3074-4df8-8548-c47f70a6df37" />

# 6- Web Üzerinden Görüntülendi
<img width="438" height="120" alt="Ekran görüntüsü 2025-12-27 153819" src="https://github.com/user-attachments/assets/a1333c0c-46ec-47c7-8eaf-2e022f31cb7b" />

# 7- Video Linki
https://youtu.be/nJmPQw49gD8
