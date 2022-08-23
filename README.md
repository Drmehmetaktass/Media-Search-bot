# [Media Search bot](https://github.com/Mahesh0253/Media-Search-bot)

* Satır içi arama için dizin kanalı veya grup dosyaları.
* Telegram kanalına veya grubuna dosya gönderdiğinizde, bu bot o dosyayı veritabanına kaydeder, böylece satır içi modda kolayca arama yapabilirsiniz.
* Altyazı desteği ile belge, video ve ses dosyası formatlarını destekler.

## Kurulum

### Bot oluşturmak için bu videoyu izleyin - https://youtu.be/dsuTn4qV2GA
### Kolay yol
[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://dashboard.heroku.com/new?template=https://github.com/Drmehmetaktass/Media-Search-bot)


### Zor yol
```bash
# Sanal ortam oluştur
python3 -m venv env

# Sanal ortamı etkinleştir
env\Scripts\activate.bat # Pencereler için
source env/bin/activate # Linux veya MacOS için

# Paketleri Yükle
pip3 install -r requirements.txt

# info.py'yi aşağıda verilen değişkenlerle düzenleyin ve ardından bot'u çalıştırın
python3 bot.py
```
Check [`sample_info.py`](sample_info.py) before editing [`info.py`](info.py) file

### Docker
```
docker run -d \
    -e BOT_TOKEN="123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11" \
    -e API_ID='12345' \
    -e API_HASH='0123456789abcdef0123456789abcdef' \
    -e CHANNELS='-10012345678' \
    -e ADMINS='123456789' \
    -e DATABASE_URI="mongodb+srv://...mongodb.net/Database?retryWrites=true&w=majority" \
    -e DATABASE_NAME=databasename \
    --restart on-failure \
    --name mediasearchbot botxtg/media-search-bot
```
You can also run with `env` file like below,
```
docker run -d \ 
     --env-file .env \
     --restart on-failure \
     --name mediasearchbot botxtg/media-search-bot
```

## Değişkenler
### Gerekli Değişkenler
* `BOT_TOKEN`: kullanarak bir bot oluşturun [@BotFather](https://telegram.dog/BotFather), and get the Telegram API token.
* `API_ID`: Bu değeri şuradan alın: [telegram.org](https://my.telegram.org/apps)
* `API_HASH`: Bu değeri şuradan alın: [telegram.org](https://my.telegram.org/apps)
* `CHANNELS`: Kanal veya grubun kullanıcı adı veya kimliği. Birden çok kimliği boşlukla ayırın
* `YÖNETİCİLER`: Yöneticinin Kullanıcı Adı veya Kimliği. Birden çok Yöneticiyi alana göre ayırın
* `DATABASE_URI`: [mongoDB](https://www.mongodb.com) URI. Bu değeri şuradan alın: [mongoDB](https://www.mongodb.com). Daha fazla yardım için bunu izleyin [video](https://youtu.be/dsuTn4qV2GA)
* `DATABASE_NAME`: Name of the database in [mongoDB](https://www.mongodb.com). For more help watch this [video](https://youtu.be/dsuTn4qV2GA)

### Opsiyonel Değişkenler
* `COLLECTION_NAME`: Koleksiyonların adı. Varsayılan olarak Telegram_files'dir. Aynı veritabanını kullanacaksanız, her bot için farklı koleksiyon adı kullanın.
* `CACHE_TIME`: r'nin saniye cinsinden maksimum süre bot, arama sonuçlarını iyileştirmek için altyazı kullanmalıdır. (Doğru yanlış)
* `AUTH_USERS`: Satır içi aramaya erişim sağlayacak kullanıcıların kullanıcı adı veya kimliği. Birden çok kullanıcıyı alana göre ayırın. Yapmıyorsanız boş bırakın Bu kanala abone olan kullanıcılar bot kullanamaz.
* `START_MSG`: Başlat komutu için hoş geldiniz mesajı.
* `INVITE_MSG`: Yetkilendirme kanalı davet mesajı.
* `USERBOT_STRING_SESSION`: Kullanıcı bot dizisi oturumu.
## Yönetici komutları
```
channel - Kanallar hakkında temel bilgileri alın
total - Kaydedilen dosyaların toplamını göster
Delete - Dosyayı veritabanından sil
index - Kanaldaki veya gruptaki tüm dosyaları indeksle
logger - Günlük dosyasını 
```
 
## İpuçları
* Veritabanında henüz indekslenmemiş eski dosyaları kaydetmek için `index` komutunu kullanın veya [one_time_indexer.py](one_time_indexer.py) dosyasını çalıştırın.
* Yapabilirsiniz use `|` Belirli bir dosya türünü ararken sorgu ve dosya türünü ayırmak için. Örneğin: `Yenilmezler | video'
* Bir kanal veya grup oluşturmak istemiyorsanız, kanal olarak sohbet kimliğinizi / kullanıcı adınızı kullanın. 
## Katkılar
Katkılara açığız.

## teşekkürler [Pyrogram](https://github.com/pyrogram/pyrogram)

## Support
[Update Channel](https://t.me/turkcbot) and [Support Group](https://t.me/marvelturkey)

## License
Code released under [The GNU General Public License](LICENSE).

