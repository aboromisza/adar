# adar
ideiglenes
enable secret "jelszó"
username vmi password valami
service password-encryption

ip domain-name 
crypto key generate rsa (1024)
ip ssh version 2
line consol 0
login local
 
line vty 0 15
login local
transport input ssh 
do wr
interface vlan 1 ip address
no shutdown
ip default-gateway  
banner motd " "
copy startup-config tftp:
interfacef0/1
ipv6 address 
ipv6 unicast-routing
ipv6 address  link-local
show running-config
vlsmcalc.com

f = open("demofile.txt", "w")
lista = ""
for i in range(1000):
    lista += str(i) + ";"
f.write(lista)

f.close()

#open and read the file after the appending:
f = open("demofile.txt", "r")
print(f.read())

with open("probaszamok.txt", "w") as kimenet:
    index = 0
    for i in lista:
        if index < len(lista)-1:
            kimenet.write(str(i) + ";")
            index += 1
        else:
            kimenet.write(str(i))
            

file = open("probaszamok.txt")
for i in file:
    seged = ','.join(i.strip().split(";"))
    
    alapszo = "zorglub"
print(fordito(alapszo))
print(alapszo[::-1])

tukorlista = []
for betu in alapszo:
  tukorlista.insert(0, betu)

print(''.join(tukorlista))


def fordito(szo):
  tlista=[]
  for betu in szo:
    tlista.insert(0, betu)
  print("".join(tlista))

szo = input('Írd be a tükrözni kívánt szót! : ')
fordito(szo)


# A beolvasott szöveget írasd ki szavanként külön sorba!'''

szoveg = 'A beolvasott szöveget írasd ki szavanként külön sorba!'
szoveg_lista = szoveg.split()
print('\n'.join(szoveg_lista))'''

# Olvasson be stringeket ”*” végjelig. Írja ki a leghosszabbat és a legnagyobbat!

ezek_sztringek = "Kávéfőző*Uborka*auto*Politikus*Rebarbara*csiga*elon musk"

def sztring_vizsgalo(x):
    hossz = 0
    leghosszabb = ''
    sz_lista = x.split('*')
    for szo in sz_lista:
        if hossz < len(szo):
            leghosszabb = szo
    print(f'A leghoszabb a(z) {leghosszabb} szó.')
    sz_lista.sort()
    print(f'A legnagyobb pedig a(z) {(sz_lista[0])} szó, bármit is jelentsen a "legnagyobb"')
3
sztring_vizsgalo(ezek_sztringek)


# Vowel eater – ”magánhangzó evő” – a beolvasott szöveget írd ki magánhangzók nélkül!

def hangzo_killer(szo):
    maganhangzok = 'a, á, e, é, i, í, o, ó, ö, ő, u, ú, ü, ű'  # azért nem lista eleve, mert így volt a wikin :)
    maganhangzok_lista = maganhangzok.split(', ')
    szo2 = ""
    for i in range(len(szo)):
        if szo[i] not in maganhangzok_lista:
            szo2 += szo[i]
    print(szo2)

hangzo_killer(input('Add meg a magánhangó-purgálni kívánt szót! '))


# Tölts fel egy listát 10 véletlenszámmal úgy, hogy ne legyenek ismétlődések benne!


szamlista =[]

while (len(szamlista)) != 10:
   szam = random.randint(1, 100)
   if szam not in szamlista:
       szamlista.append(szam)
print(szamlista)
