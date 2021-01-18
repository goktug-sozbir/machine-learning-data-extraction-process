# machine-learning-data-extraction-process

PROBLEM:
Emlak365 adlı siteden; toki haberleri, konut kredisi, gündem, emlak magazin, taksit kredisi, gezi seyahat, kampanyalar sayfalarının içerisindeki haberlerin başlıklarını veri seti haline getirmek amaçlanmıştır.

CRAWLER:
-Requests i  get metodu için kullandım. 
source = requests.get('https://www.emlak365.com/toki- haberleri/page/1#horizontal_news').text	
-BeautifulSoup metodunu veri çekerken kullandım.
soup = BeautifulSoup(source,'lxml') 
for veriseti in soup.find_all('div',class_='hs-item-caption'):
   baslık=veriseti.find('div', class_='hs-item-title hs-title-font')
   csv_writer.writerow([baslık.text])
   
VERİ SETİ:
Çekilen veri sayısı 523. Veriler işlendikten sonra toplam sayı 1043 olmaktadır. Bu veriler baslik adı altında sıralanmaktadır. Haberlerin başlıklarını elde etmiş oluruz.

ÖN İŞLEME:
Nltk kütüphanesinin Word_tokenizer özelliğini kullanarak cümleleri kelimelere ayırdım.
csv_file = open('anahamişlenmiş.csv','w',newline="")
csv_writer=csv.writer(csv_file)
with open('anahamveri.csv', 'r') as csvfile:  
    reader = csv.reader(csvfile)
    for row in reader:
       for cumle in row:
          df=cumle
          tokenizedwords = nltk.word_tokenize(df)
          csv_writer.writerow([df])
csv_file.close()
csv_file =open('anahamveri.csv', 'a+', newline='')
csv_writer=csv.writer(csv_file)
with open('anahamişlenmiş.csv', 'r') as csvfile: 
    reader = csv.reader(csvfile)
    for row in reader:
       for cumle in row:
          df=cümle
