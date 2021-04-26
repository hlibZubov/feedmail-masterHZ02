# Feedmail

WebApp wrote in node js and vanilla js for sending rss via email

## Installation

Tworzymy App Service i Cosmos DB
![Alt Text](https://github.com/hlibZubov/feedmail-masterHZ02/blob/main/2.PNG)
![Alt Text](https://github.com/hlibZubov/feedmail-masterHZ02/blob/main/3.PNG)

1.	Pobieramy program z linka jako zip https://github.com/bp-wsb/feedmail
2.	Wchodzimy  feedmail-master-> .github -> workflows -> master_wsb-feedmail
```bash
app-name: 'wsb-feedmail'
        slot-name: 'production'
        publish-profile: ${{ secrets.AzureAppService_PublishProfile_fe5bdf53ec8f49d290ed7add8239d11b }}
        package: .
```
Zamieniamy wsb- feedmail' na swój AppService w naszym przypadku FeedmailHZ02
![Alt Text](https://github.com/hlibZubov/feedmail-masterHZ02/blob/main/1.PNG)
```bash
app-name: 'FeedmailHZ02'
        slot-name: 'production'
        publish-profile: ${{ secrets.AZURE_WEBAPP_PUBLISH_PROFILE }}
        package: .

```
Po czym wrzucamy na Git hub-a

Po tym idziemy do Settings i dodajemy New Secret o nazwie AZURE_WEBAPP_PUBLISH_PROFILE
![Alt Text](https://github.com/hlibZubov/feedmail-masterHZ02/blob/main/4.PNG)
Value pobieramy z AppService -> Get publish profile I pobieramy, dodajemy wszystko do Value
![Alt Text](https://github.com/hlibZubov/feedmail-masterHZ02/blob/main/5.PNG)
![Alt Text](https://github.com/hlibZubov/feedmail-masterHZ02/blob/main/6.PNG)
Push do repozytorium z aplikacją
Dodajemy zmienne środowiskowe do App Service
![Alt Text](https://github.com/hlibZubov/feedmail-masterHZ02/blob/main/7.PNG)
NODE_ENV value zostawiamy puste
NODE_CONFIG with value

      {
          "feedmail": {
              "db": {
                  "url": "", 
                  "name": "prod", 
                  "options": {
                  "useUnifiedTopology": true 
                  }
              },
              "logger": {
                  "level": "debug",
                  "filename": "./backend.log"
              },
              "mailgun": {
                  "domain": "",
                  "apiKey": ""
              }  
          }
      }
W url wpisujemy link do podłączenia Cosmosdb
W domain wpisujemy domene jaka dostalismy w mailgunie
W apiKey wpisujemy privatApi key ktory dostalismy w mailgunie
![Alt Text](https://github.com/hlibZubov/feedmail-masterHZ02/blob/main/8.PNG)

- # Testy
- - # loadPage
![Alt Text](https://github.com/hlibZubov/feedmail-masterHZ02/blob/main/test/loadPage.PNG)
- - # getMail
![Alt Text](https://github.com/hlibZubov/feedmail-masterHZ02/blob/main/test/getMail.PNG)
- - # getUser
![Alt Text](https://github.com/hlibZubov/feedmail-masterHZ02/blob/main/test/getUser.PNG)
- - # postMail
![Alt Text](https://github.com/hlibZubov/feedmail-masterHZ02/blob/main/test/postMail.PNG)
- - # postUser
![Alt Text](https://github.com/hlibZubov/feedmail-masterHZ02/blob/main/test/postUser.PNG)
