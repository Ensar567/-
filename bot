import discord
from discord.ext import commands
import discord.ext
from passcreate import pass_generate
from discord import app_commands
import time as t
import random
import requests
#----------------------------------------------------------------Import---------------------------------------#
Bot = commands.Bot(command_prefix= "." , intents= discord.Intents.all())   #Bota bütün yetkileri verir 
#--------------------------------------------------Def--------------------------------------------------#


def get_duck_image_url():    
    url = 'https://random-d.uk/api/random'
    res = requests.get(url)
    data = res.json()
    return data['url']

def get_dog_image_url():
    url = 'https://random.dog/woof.json'
    res = requests.get(url)
    data = res.json()
    return data['url']


#----------------------------------------------Commands----------------------------------------------#


@Bot.command()
async def söyle(ctx,message): #Komutun adı ve parametreler  | Message komutu kullandktan sonra bosluk bırakıp yazdıgı mesaj
    await ctx.message.delete() #En son mesajı siler yani kullanıcının yazdıgını
    await ctx.send(message)   #Kullanıcının Yazdıgı mesajı yazar 


@Bot.command()
async def sil(ctx,mesaj_sil: int):
    if mesaj_sil < 0:
        await ctx.send("Please enter avaliable integar")
    else:
        await ctx.channel.purge(limit=mesaj_sil+1)
        embed = discord.Embed(title="Purge",description="**Chat succesfully cleared.**",color=discord.Colour.red())
        await ctx.send(embed=embed)
        await ctx.message.delete()    


@Bot.command()
async def mem(ctx):
    with open('images/mem.png','rb') as f:
        picture = discord.File(f)
    await ctx.send(file=picture)


@Bot.command('duck')
async def duck(ctx):
    '''duck komutunu çağırdığımızda, program ordek_resmi_urlsi_al fonksiyonunu çağırır.'''
    image_url = get_duck_image_url()
    await ctx.send(image_url)



@Bot.command('dog')
async def dog(ctx):
    image_url = get_dog_image_url()
    await ctx.send(image_url)
    


@Bot.command()
async def atık(ctx,atik_turu):
    if atik_turu == 'çevre':
        await ctx.send('**Atıkların düzenli depolanması ve bertarafı çevre kirliliğine yol açar. Atık miktarının azaltılması, çevre kirliliğinin önlenmesine yardımcı olur. Özellikle tehlikeli atıkların azaltılması, su ve toprak kirliliğini önler ve doğal ekosistemlerin korunmasına katkı sağlar.**')
        with open('images/çevrejpg.jpg','rb') as f:
            picture = discord.File(f)
            await ctx.send(file=picture)

    elif atik_turu == 'ekonomik':
        await ctx.send('**Atık miktarının azaltılması, ekonomik açıdan da fayda sağlar. Atıkların geri dönüşümü ve yeniden kullanımı, malzeme ve kaynak tasarrufu sağlar. Bu da maliyetleri düşürür ve işletmelere veya hanelere tasarruf sağlar. Ayrıca, geri dönüşüm sektörü de istihdam yaratır ve ekonomik büyümeye katkıda bulunur.**')
        with open('images/ekonomik.jpg','rb') as f:
            picture = discord.File(f)
            await ctx.send(file=picture)  

    elif atik_turu == 'kaynak':
        await ctx.send('**Atık miktarının azaltılması, doğal kaynakların daha verimli kullanılmasını sağlar. Üretim için kullanılan hammaddelerin azaltılması, enerji tasarrufu ve doğal kaynakların sürdürülebilirliği için önemlidir. Atık miktarının azaltılması, gelecek nesillerin de kaynaklardan yararlanabilmesini sağlar.**')
        with open('images/kaynaktüketim.jpg','rb') as f:
            picture = discord.File(f)
            await ctx.send(file=picture)
            
    elif atik_turu == 'kararsızım':
        await ctx.send("Şunlara Bakabilirsin. (**kaynak** , **ekonomi** veya  **çevre**)")
























@Bot.tree.command(name="yardım", description="Bu Komut Size Bot Hakkında Yardımcı Olur") #Komutun Tanıtımı
async def yardım(interaction=discord.Interaction):   
    await interaction.response.send_message("Şuanlık komutlarımız yapımda ", #Cevap Olarak Mesaj gönderir
    ephemeral=True) #Kişinin sadece kendisi görmsesi sağlanır




















@Bot.event
async def on_ready():
    print(f'{Bot.user} olarak giriş yaptık.')
    try:
        synced = await Bot.tree.sync()
        print(f"Synced{len(synced)} commands")
    except Exception as e:
        print(e)













#-----Run-----#
Bot.run("TOKEN")
