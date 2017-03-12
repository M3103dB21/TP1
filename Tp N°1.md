# TP1

### Creation de serveur UDP
Tout d'abord nous avons crée un serveur permettant de recevoir un message d'un client (détaillé a la suite), mettre en majuscule ce message et le renvoyer au client.
```Python
from socket import *

serverPort = 12000
serverSocket = socket(AF_INET, SOCK_DGRAM)
serverSocket.bind(('', serverPort))
print "The server is ready to receive"
while 1:
	message, clientAddress = serverSocket.recvfrom(2048)
	modifiedMessage = message.upper()
	serverSocket.sendto(modifiedMessage, clientAddress)
```
  
### Creation d'un client UDP

Le client permet d'envoyer un message au serveur, dans notre cas, ou à n'importe quel adresse IP : Port.
```Python
from socket import *

serverName = "localhost"
serverPort = 12000

clientSocket = socket(AF_INET, SOCK_DGRAM)
message = raw_input('Texte:')
clientSocket.sendto(message,(serverName, serverPort))
modifiedMessage, serverAddress = clientSocket.recvfrom(2048)
print modifiedMessage
clientSocket.close()
```
