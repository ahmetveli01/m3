import discord
# ayricaliklar (intents) değişkeni botun ayrıcalıklarını depolayacak
intents = discord.Intents.default()
# Mesajları okuma ayrıcalığını etkinleştirelim
intents.message_content = True
# client (istemci) değişkeniyle bir bot oluşturalım ve ayrıcalıkları ona aktaralım
client = discord.Client(intents=intents)


el_isi_fikirleri= [
    "Plastik şişelerden çiçek saksısı yapabilirsiniz",
    "Plastik bardaklardan avize yapabilirisniz",
    "Pet şişelerden ayakkabı yapımı",
    "Pet şişeleri kullarak hayvanlar içim yem yapımı",
    "Kartonlardan kedilere ev yapımı",
    "Kartonlardan futbol kupası yapımı"
]



geri_donusum_rehberi ={
    "Plastik şişe":"Geri dönüştürülebilir. Plastik atık kutusuna atın.",
    "cam":"Geri dönüştürülebilir. Cam atık kutusuna atın.",
    "karton":"Geri dönüştürülebilir. Karton atık kutusuna atın.",
    "metal":"Geri dönüştürülebilir. Metal atık kutusuna atın.",
    "yag":"Geri dönüştürülebilir. Yağ atık kutusuna atın.",
    "pil":"Geri dönüştürülebilir. Pil atık kutusuna atın."
}


ayrisma_sureleri ={
    "plastik": "450 yıl",
    "cam": " 4000 yıl",
    "karton":"12 yıl"
}


@client.event
async def on_ready():
    print(f'{client.user} olarak giriş yaptık.')

@client.event
async def on_message(message):
    if message.author == client.user:
        return
    
    if message.content.startswith('$1.adım'):
        await message.channel.send("Atiklarinizi Ayriştirin")
    elif message.content.startswith("$2.adım"):
        await message.channel.send("Cam Kullanimina Ağirlik Verin")
    elif message.content.startswith("$3.adım"):
        await message.channel.send("Gıdaları Kompost Yapı")
    elif message.content.startswith("$4.adım"):
        await message.channel.send("Tek Kullanımlık Ürünlerden Kaçının") 
    elif message.content.startswith("$5.adım"):
        await message.channel.send("atık kutulardan geri dönüşüm kutusu yapabilirsin")
    elif message.content.startswith("$6.adım"):
        await message.channel.send("etrafınızdaki diğer insanlarıda bu konuyla ilgili bilgilendirin")
    elif message.content.startswith("$7.adım"):
        await message.channel.send("Plastik şişelerden çiçek saksısı yapabilirsiniz")
    elif message.content.startswith("$8.adım"):
        await message.channel.send("Plastik bardaklardan avize yapabiliriz")
    elif message.content.startswith("$9.adım"):
        await message.channel.send("Pet şişelerden ayakkabı yapımı")
    elif message.content.startswith("$10.adım"):
        await message.channel.send("Pet şişeleri kullarak hayvanlar içim yem yapımı")
    elif message.content.startswith("$11.adım"):
        await message.channel.send("Kartonlardan kedilere ev yapımı")
    elif message.content.startswith("$12.adım"):
        await message.channel.send("Kartonlardan futbol kupası yapımı")

    elif message.content.startswith("$elisi"):
        fikir= random.choice(el_isi_fikirleri)
        await message.channel.send(f"El İşi Fikri: {fikir}")
    
    elif message.content.startswith("$geri"):
        item = message.content[len("$geri "):].lower()
        if item in geri_donusum_rehberi:
            await message.channel.send(geri_donusum_rehberi[item])
        else:
             await message.channel.send("Anladığımdan emin değilim, rehbere bak lütfen..")

    elif message.content.startswith("$ayrisma"):
        item = message.content[len("$ayrisma "):].lower()
        if item in ayrisma_sureleri:
            await message.channel.send(ayrisma_sureleri[item])
        else:
             await message.channel.send("Yanlış bilgi yazdınız lütfen tekrar deneyiniz..")

    else:
        await message.channel.send("sorunuzu anlamadım, lütfen $1.adım,$2.adım ... şeklinde yazın , Kelimelere başlamdan önce dolar işaretini unutma") 

client.run("    token     ")
