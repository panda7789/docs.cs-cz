---
title: Naslouchání pomocí soketů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- sockets, listening with sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- protocols, sockets
- listening with sockets
- Internet, sockets
ms.assetid: 40e426cc-13db-4371-95eb-f7388bd23ebf
ms.openlocfilehash: cf8316ede6888b99a8b0c87cfa3426b33be18b7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180744"
---
# <a name="listening-with-sockets"></a>Naslouchání pomocí soketů
Naslouchací proces nebo sokety serveru otevřou port v síti a počkejte, až se klient k tomuto portu připojí. Přestože existují jiné rodiny síťových adres a protokoly, tento příklad ukazuje, jak vytvořit vzdálenou službu pro síť TCP/IP.  
  
 Jedinečná adresa služby TCP/IP je definována kombinací IP adresy hostitele s číslem portu služby a vytvořením koncového bodu pro službu. Třída <xref:System.Net.Dns> poskytuje metody, které vracejí informace o síťových adresách podporovaných místním síťovým zařízením. Pokud má místní síťové zařízení více než jednu síťovou adresu nebo pokud místní systém podporuje více než jedno síťové zařízení, vrátí třída **DNS** informace o všech síťových adresách a aplikace musí zvolit správnou adresu služby. Internetová autorita pro přiřazená čísla (Iana) definuje čísla portů pro běžné služby; Další informace naleznete v [tématu Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/port-numbers). Ostatní služby mohou mít registrovaná čísla portů v rozsahu 1 024 až 65 535.  
  
 Následující příklad vytvoří <xref:System.Net.IPEndPoint> pro server kombinací první IP adresy vrácené **službou DNS** pro hostitelský počítač s číslem portu vybraným z rozsahu registrovaných čísel portů.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.GetHostEntry(Dns.GetHostName())  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.GetHostEntry(Dns.GetHostName());  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
```  
  
 Po určení místního koncového <xref:System.Net.Sockets.Socket> bodu musí být přidružený <xref:System.Net.Sockets.Socket.Bind%2A> k tomuto koncovému bodu pomocí <xref:System.Net.Sockets.Socket.Listen%2A> metody a nastavit naslouchání na koncovém bodu pomocí metody. **Vazba** vyvolá výjimku, pokud je konkrétní kombinace adresy a portu již používána. Následující příklad ukazuje spojení **Socket** s **IPEndPoint**.  
  
```vb  
Dim listener As New Socket(ipAddress.AddressFamily, _  
    SocketType.Stream, ProtocolType.Tcp)
listener.Bind(localEndPoint)  
listener.Listen(100)  
```  
  
```csharp  
Socket listener = new Socket(ipAddress.AddressFamily,
    SocketType.Stream, ProtocolType.Tcp);
listener.Bind(localEndPoint);  
listener.Listen(100);  
```  
  
 Metoda **Listen** přebírá jeden parametr, který určuje, kolik čekajících připojení k **Socket** uvolňuje před vrácením chyby zaneprázdněnserveru připojujícímu se klientovi. V tomto případě je do fronty připojení umístěno až 100 klientů před vrácením odpovědi serveru zaneprázdněn na číslo klienta 101.  
  
## <a name="see-also"></a>Viz také

- [Použití synchronního serverového soketu](using-a-synchronous-server-socket.md)
- [Použití asynchronního serverového soketu](using-an-asynchronous-server-socket.md)
- [Použití klientských soketů](using-client-sockets.md)
- [Postupy: Vytvoření soketu](how-to-create-a-socket.md)
- [Sokety](sockets.md)
