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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: c518c3bea980e23367477bd1b9851630454b728b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47209883"
---
# <a name="listening-with-sockets"></a>Naslouchání pomocí soketů
Naslouchací proces nebo server sockets otevření portu v síti a potom počkejte klienta pro připojení k tomuto portu. I když existují jiné rodiny adres sítě a protokoly, tento příklad ukazuje, jak vytvořit vzdálené služby pro sítě TCP/IP.  
  
 Díky kombinaci IP adresu hostitele s použitím čísla portu služby vytvořit koncový bod služby je definován jedinečnou adresu služby TCP/IP. <xref:System.Net.Dns> Třída poskytuje metody, které vracejí informace o síťové adresy místní síťové zařízení podporuje. Když zařízení místní sítě má více než jednu síťovou adresu, nebo místní systém podporuje více než jedno síťové zařízení, **Dns** třída vrací informace o všech síťových adres, a aplikace musíte vybrat správné Adresa pro službu. Internet Assigned Numbers Authority (Iana) definuje čísla portů pro běžné služby; Další informace najdete v tématu [název služby a registru číslo portu protokolu přenosu](https://www.iana.org/assignments/port-numbers). Další služby můžou jste se zaregistrovali čísla portu v rozsahu 1 024 do 65 535.  
  
 Následující příklad vytvoří <xref:System.Net.IPEndPoint> pro server kombinací první IP adresu vrácenou **Dns** pro hostitelský počítač s číslem portu zvolit rozsah čísel registrovaných portů.  
  
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
  
 Po místním koncovým bodem je určit, <xref:System.Net.Sockets.Socket> musí být přidružen pomocí tohoto koncového bodu <xref:System.Net.Sockets.Socket.Bind%2A> metoda a nastavte tak, aby naslouchala na koncový bod pomocí <xref:System.Net.Sockets.Socket.Listen%2A> metoda. **Vytvoření vazby** vyvolá výjimku, pokud se konkrétní kombinaci adresu a port je již používán. Následující příklad ukazuje přidružení **soketu** s **IPEndPoint**.  
  
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
  
 **Naslouchání** metoda přijímá jeden parametr, který určuje, kolik čeká na připojení k **soketu** jsou povoleny před chybu zaneprázdněný server se vrátí do připojujícího se klienta. V takovém případě až 100 klientů jsou umístěné ve frontě připojení předtím, než je server zaneprázdněný odpověď se vrátí do klienta číslem 101.  
  
## <a name="see-also"></a>Viz také  
 [Použití synchronního serverového soketu](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)  
 [Použití asynchronního serverového soketu](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [Použití klientských soketů](../../../docs/framework/network-programming/using-client-sockets.md)  
 [Postupy: Vytvoření soketu](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
 [Sokety](../../../docs/framework/network-programming/sockets.md)
