---
title: Naslouchání s Sockets
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f85b63b151bcc20db635f56ec1dfec8df6c92241
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395775"
---
# <a name="listening-with-sockets"></a>Naslouchání s Sockets
Naslouchací proces nebo server sockets otevřít port v síti a potom počkejte, než pro klienta pro připojení k tomuto portu. I když existují další rodiny adres sítě a protokoly, tento příklad ukazuje postup vytvoření vzdálené služby pro sítě TCP/IP.  
  
 Definuje jedinečnou adresu služby TCP/IP kombinování IP adresu hostitele se číslo portu služby k vytvoření koncového bodu služby. <xref:System.Net.Dns> Třída poskytuje metody, které vracejí informace o síťové adresy nepodporuje místní síťové zařízení. Když je zařízení místní sítě s více než jednu síťovou adresu, nebo pokud místní systém podporuje více než jedno síťové zařízení, **Dns** třída vrací informace o všech síťových adres, a aplikace, musíte zvolit správnou Adresa pro službu. Internet Assigned Numbers Authority (Iana) definuje čísla portů pro běžné služby (pro další informace najdete v tématu www.iana.org/assignments/port-numbers). Další služby můžete zaregistrovat čísla portů v rozsahu 1 024 jednotek do 65 535.  
  
 Následující příklad vytvoří <xref:System.Net.IPEndPoint> pro server kombinací první IP adresu vrácenou **Dns** pro hostitelský počítač s číslem portu vybrali z rozsahu čísla registrovaných portů.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
```  
  
 Po místní koncový bod je určit, <xref:System.Net.Sockets.Socket> musí být přidružený tento koncový bod pomocí <xref:System.Net.Sockets.Socket.Bind%2A> metoda a sady pro naslouchání na koncový bod pomocí <xref:System.Net.Sockets.Socket.Listen%2A> metoda. **Vytvoření vazby** vyvolá výjimku, pokud konkrétní kombinace adresy a portu je již používán. Následující příklad ukazuje, přiřazení **soketu** s **IPEndPoint**.  
  
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
  
 **Naslouchání** metoda přebírá jediný parametr, který určuje, kolik čeká na připojení k **soketu** jsou povoleny před připojujícího se klienta se vrátí zaneprázdněn chybu serveru. V takovém případě až 100 klientů jsou umístěny ve frontě připojení před zaneprázdněn odpověď serveru je vrácen do klienta číslem 101.  
  
## <a name="see-also"></a>Viz také  
 [Použití synchronního serverového soketu](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)  
 [Použití asynchronního serverového soketu](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [Použití klientských soketů](../../../docs/framework/network-programming/using-client-sockets.md)  
 [Postupy: Vytvoření soketu](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
 [Sokety](../../../docs/framework/network-programming/sockets.md)
