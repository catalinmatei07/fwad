UNIVERSITATEA DE STAT DIN MOLDOVA

FACULTATEA  MATEMATICĂ ŞI INFORMATICĂ DEPARTAMENTUL INFORMATICĂ



Matei Catalin IAFR2101



Laboratorul nr. 1
la disciplina Framework-uri Pentru Dezvoltarea Web




Chişinău,  2024

 


Sarcina nr. 1. Analiza cererilor HTTP
1.	Accesați site-ul http://sandbox.usm.md/login. 
2.	Deschideți fila Network în instrumentele pentru dezvoltatori ale browserului.
3.	Introduceți date incorecte pentru autentificare (de exemplu, username: student, password: studentpass).
4.	Analizați cererile care au fost trimise către server.
 <img width="1196" alt="image" src="https://github.com/user-attachments/assets/a2b518b9-7aeb-4b92-9f32-e175b464be06">

5.	Răspundeți la următoarele întrebări:
o	Ce metodă HTTP a fost utilizată pentru a trimite cererea?
POST
o	Ce anteturi au fost trimise în cerere?
accept:
*/*
accept-encoding:
gzip, deflate
accept-language:
en-GB,en-US;q=0.9,en;q=0.8
connection:
keep-alive
content-length:
37
content-type:
application/x-www-form-urlencoded; charset=UTF-8
host:
sandbox.usm.md
origin:
http://sandbox.usm.md
referer:
http://sandbox.usm.md/login/
user-agent:
Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/131.0.0.0 Mobile Safari/537.36
x-requested-with:
XMLHttpRequest
o	Ce parametri au fost trimiși în cerere?
 <img width="657" alt="image" src="https://github.com/user-attachments/assets/02a803bf-74d7-42bd-879d-197c2861ded6">

o	Ce cod de stare a fost returnat de server?
Status Code: 401 Unauthorized
o	Ce anteturi au fost trimise în răspuns?
connection:
keep-alive
content-type:
text/plain;charset=UTF-8
date:
Tue, 03 Dec 2024 13:22:22 GMT
server:
nginx/1.24.0 (Ubuntu)
transfer-encoding:
chunked

6.	Repetați pașii 3-5, introducând date corecte pentru autentificare (username: admin, password: password).
 


1. admin / password
 <img width="569" alt="image" src="https://github.com/user-attachments/assets/7103a7e4-f36b-4c6a-9981-431f1deb3673">

 


2. admin / password2
 
 <img width="506" alt="image" src="https://github.com/user-attachments/assets/642419a5-6fe6-48e0-b9b5-b8db19c6fc93">



 

3.  catalin / matei
 <img width="493" alt="image" src="https://github.com/user-attachments/assets/0199384b-f701-457c-ad37-97721ffee5a4">

 
 
Sarcina nr. 2. Crearea cererilor HTTP


1.	Scrieți o cerere de tip GET către server la adresa http://sandbox.com, indicând în antetul User-Agent numele și prenumele dvs.

curl -X GET http://sandbox.com -H "User-Agent: Matei Catalin"

2.	Scrieți o cerere de tip POST către server la adresa http://sandbox.com/cars, indicând în corpul cererii următorii parametri:
o	make: Toyota
o	model: Corolla
o	year: 2020

curl -X POST http://sandbox.com/cars -d "make=Toyota&model=Corolla&year=2020"

3.	Scrieți o cerere de tip PUT către server la adresa http://sandbox.com/cars/1, indicând în antetul User-Agent numele și prenumele dvs., în antetul Content-Type valoarea application/json, iar în corpul cererii următorii parametri:

{
   "make": "Toyota",
   "model": "Corolla",
   "year": 2021
}

curl -X PUT http://sandbox.com/cars/1 \
-H "User-Agent: Matei Catalin" \
-H "Content-Type: application/json" \
-d '{"make": "Toyota", "model": "Corolla", "year": 2021}'

4.	Scrieți unul dintre posibilele răspunsuri ale serverului la cererea anterioară.

HTTP/1.1 200 OK
Content-Type: application/json
{
   "message": "Car updated successfully",
   "id": 1,
   "data": {
      "make": "Toyota",
      "model": "Corolla",
      "year": 2021
   }
}

 
200 (OK): Resursa a fost procesată cu succes (e.g., o actualizare s-a efectuat corect).
201 (Created): Resursa a fost creată cu succes (e.g., un nou element a fost adăugat la /cars).
400 (Bad Request): Cererea este formatată greșit (e.g., lipsesc parametri obligatorii sau corpul cererii are erori).
401 (Unauthorized): Autentificarea este necesară, dar nu a fost furnizată sau este invalidă.
403 (Forbidden): Utilizatorul nu are permisiunea de a accesa resursa.
404 (Not Found): Resursa solicitată nu există pe server (e.g., /cars/1 nu este disponibilă).
500 (Internal Server Error): O eroare neașteptată s-a produs pe server.


5.	Scrieți o cerere de tip DELETE la alegerea dvs. și să explicați de ce, în acest caz, este potrivit să utilizați metoda DELETE

curl -X DELETE http://sandbox.com/cars/1

Metoda DELETE este potrivită pentru a șterge resurse, cum ar fi o mașină cu ID-ul 1. Utilizarea acestei metode este justificată deoarece ștergerea unei resurse este o acțiune specifică și clară, asociată cu acest tip de cerere
 
Sarcina nr. 3. Sarcina suplimentară. HTTP_Quest

1.	Trimiteți o cerere de tip POST către server la adresa http://sandbox.usm.md/quest, indicând în antetul User-Agent numele și prenumele dvs. (De exemplu, User-Agent: John Doe).

POST /quest HTTP/1.1
Host: sandbox.usm.md
User-Agent: John Doe
curl:
curl -X POST http://sandbox.usm.md/quest -H "User-Agent: Matei Catalin "

2.	Urmați instrucțiunile de pe server, îndeplinindu-le în ordine.
3.	La finalul quest-ului, vi se va afișa un cuvânt secret, pe care va trebui să-l includeți în raport.

id: 147225
token: BAAZMQFFAQQHFSUIAw==


 
Întrebări de autoevaluare
1. Ce este protocolul HTTP?
HTTP (Hypertext Transfer Protocol) este un protocol folosit pentru a transfera date între un client (ex. browser) și un server. Este baza web-ului, folosit pentru accesarea site-urilor și descărcarea resurselor.
2. Pentru ce folosim antetul User-Agent?
Antetul User-Agent identifică aplicația care face cererea (ex. browser, aplicație). Serverul îl folosește pentru a adapta răspunsul sau pentru a colecta informații despre dispozitive.
3. Care este diferența dintre metodele PUT și PATCH?
•	PUT: Înlocuiește complet o resursă.
•	PATCH: Modifică doar anumite părți ale unei resurse.

