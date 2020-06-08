---
title: Naslouchání pomocí soketů
description: Naučte se, jak vytvořit vzdálenou službu, kde soket serveru otevírá port v síti a čeká, až se klient připojí k tomuto portu.
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
ms.openlocfilehash: 0b6de67772bae397373e307ec02ce69a71b0542e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502311"
---
# <a name="listening-with-sockets"></a>Naslouchání pomocí soketů
Naslouchací proces nebo serverové sokety otevřou port v síti a pak čekají na připojení klienta k tomuto portu. I když existují další řady síťových adres a protokoly, tento příklad ukazuje, jak vytvořit vzdálenou službu pro síť TCP/IP.  
  
 Jedinečná adresa služby TCP/IP je definovaná kombinací IP adresy hostitele s číslem portu služby, aby se vytvořil koncový bod pro službu. <xref:System.Net.Dns>Třída poskytuje metody, které vracejí informace o síťových adresách podporovaných místním síťovým zařízením. Pokud má místní síťové zařízení více než jednu síťovou adresu nebo pokud místní systém podporuje více než jedno síťové zařízení, vrátí třída **DNS** informace o všech síťových adresách a aplikace musí zvolit správnou adresu služby. Autorita pro Internet Assigned Numbers Authority (IANA) definuje čísla portů pro běžné služby. Další informace najdete v části [Service Name and Transport Protocol Number Registry](https://www.iana.org/assignments/port-numbers). Jiné služby můžou mít registrovaná čísla portů v rozsahu 1 024 až 65 535.  
  
 Následující příklad vytvoří <xref:System.Net.IPEndPoint> pro server kombinaci první IP adresy vrácené službou **DNS** pro hostitelský počítač s číslem portu vybraným z rozsahu registrovaných čísel portů.  
  
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
  
 Po určení místního koncového bodu <xref:System.Net.Sockets.Socket> musí být přidružený k tomuto koncovému bodu pomocí <xref:System.Net.Sockets.Socket.Bind%2A> metody a nastaven na naslouchání na koncovém bodu pomocí <xref:System.Net.Sockets.Socket.Listen%2A> metody. **Vazba** vyvolá výjimku, pokud se již používá specifická adresa a kombinace portů. Následující příklad ukazuje přidružení **soketu** k **IPEndPoint**.  
  
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
  
 Metoda **Listen** přijímá jeden parametr, který určuje, kolik nedokončených připojení k **soketu** je povoleno před tím, než dojde k chybě zaneprázdnění serveru v připojujícím se klientovi. V takovém případě se až 100 klientů umístí do fronty připojení před tím, než se vrátí odpověď zaneprázdněného serveru na číslo klienta 101.  
  
## <a name="see-also"></a>Viz také:

- [Použití synchronního serverového soketu](using-a-synchronous-server-socket.md)
- [Použití asynchronního serverového soketu](using-an-asynchronous-server-socket.md)
- [Použití klientských soketů](using-client-sockets.md)
- [Postupy: Vytvoření soketu](how-to-create-a-socket.md)
- [Sokety](sockets.md)
