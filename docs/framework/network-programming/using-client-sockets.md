---
title: Použití klientských soketů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- Socket class, client sockets
- protocols, sockets
- Internet, sockets
- sockets, client sockets
- client sockets
ms.assetid: 81de9f59-8177-4d98-b25d-43fc32a98383
ms.openlocfilehash: b99720b9653b8454419acd35085bfe9a7ac4b5af
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59171389"
---
# <a name="using-client-sockets"></a>Použití klientských soketů
Předtím, než můžete zahájit konverzaci prostřednictvím <xref:System.Net.Sockets.Socket>, je nutné vytvořit datový kanál mezi vaší aplikací a vzdáleným zařízením. I když existují jiné rodiny adres sítě a protokoly, tento příklad ukazuje, jak vytvořit připojení TCP/IP k vzdálené služby.  
  
 TCP/IP používá síťová adresa a číslo portu služby k jednoznačné identifikaci služby. Síťová adresa identifikuje určité zařízení v síti; číslo portu identifikuje konkrétní služby na tomto zařízení pro připojení k. Kombinace portu síťového adres a služeb se nazývá koncový bod, který je reprezentován v rozhraní .NET Framework podle <xref:System.Net.EndPoint> třídy. Potomkem **koncový bod** je definována pro každý nepodporuje rodina adres; pro rodina IP adres, je třída <xref:System.Net.IPEndPoint>.  
  
 <xref:System.Net.Dns> Třídy nabízí název domény pro aplikace, které používají protokol TCP/IP internetové služby. <xref:System.Net.Dns.Resolve%2A> Metoda dotazování DNS serveru pro namapování názvu uživatelsky přívětivé domény (například "host.contoso.com"), aby se číselné internetovou adresu (např. 192.168.1.1). **Vyřešit** vrátí <xref:System.Net.IPHostEntry> , který obsahuje seznam adres a aliasy pro požadovaný název. Ve většině případů můžete použít první adresu vrácenou v <xref:System.Net.IPHostEntry.AddressList%2A> pole. Následující kód získá <xref:System.Net.IPAddress> obsahující IP adresu pro host.contoso.com serveru.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 Internet Assigned Numbers Authority (Iana) definuje čísla portů pro běžné služby (Další informace najdete v tématu [název služby a registru číslo portu protokolu přenosu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). Další služby můžou jste se zaregistrovali čísla portu v rozsahu 1 024 do 65 535. Následující kód je kombinací IP adresu pro host.contoso.com s číslem portu, chcete-li vytvořit vzdálený koncový bod pro připojení.  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 Po určení adresa vzdáleného zařízení a vyberete port má použít pro připojení, aplikace může pokus o navázání připojení se vzdáleným zařízením. Následující příklad používá existující **IPEndPoint** pro připojení ke vzdálenému zařízení a zachytí všechny výjimky, které jsou vyvolány.  
  
```vb  
Try  
    s.Connect(ipe)  
Catch ae As ArgumentNullException  
    Console.WriteLine("ArgumentNullException : {0}", _  
        ae.ToString())  
Catch se As SocketException  
    Console.WriteLine("SocketException : {0}", se.ToString())  
Catch e As Exception  
    Console.WriteLine("Unexpected exception : {0}", e.ToString())  
End Try  
```  
  
```csharp  
try {  
    s.Connect(ipe);  
} catch(ArgumentNullException ae) {  
    Console.WriteLine("ArgumentNullException : {0}", ae.ToString());  
} catch(SocketException se) {  
    Console.WriteLine("SocketException : {0}", se.ToString());  
} catch(Exception e) {  
    Console.WriteLine("Unexpected exception : {0}", e.ToString());  
}  
```  
  
## <a name="see-also"></a>Viz také:

- [Použití synchronního klientského soketu](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)
- [Použití asynchronního klientského soketu](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)
- [Postupy: Vytvoření soketu](../../../docs/framework/network-programming/how-to-create-a-socket.md)
- [Sokety](../../../docs/framework/network-programming/sockets.md)
