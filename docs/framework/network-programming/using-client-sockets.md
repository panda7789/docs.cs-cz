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
ms.openlocfilehash: fe2ad55c3f60347369c0e92bc834d81d98f3870e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71046960"
---
# <a name="using-client-sockets"></a>Použití klientských soketů
Před zahájením konverzace prostřednictvím <xref:System.Net.Sockets.Socket>aplikace je nutné vytvořit datový kanál mezi aplikací a vzdáleným zařízením. Přestože existují jiné rodiny síťových adres a protokoly, tento příklad ukazuje, jak vytvořit připojení TCP/IP ke vzdálené službě.  
  
 Protokol TCP/IP používá k jednoznačné identifikaci služby síťovou adresu a číslo portu služby. Síťová adresa identifikuje konkrétní zařízení v síti. číslo portu identifikuje konkrétní službu na tomto zařízení, ke které se má připojit. Kombinace síťové adresy a portu služby se nazývá koncový bod, který <xref:System.Net.EndPoint> je v rozhraní .NET Framework reprezentován třídou. Potomek **EndPoint** je definován pro každou podporovanou rodinu adres; pro rodinu IP adres je <xref:System.Net.IPEndPoint>třída .  
  
 Třída <xref:System.Net.Dns> poskytuje služby názvů domén aplikacím, které používají internetové služby TCP/IP. Metoda <xref:System.Net.Dns.Resolve%2A> dotazuje server DNS na mapování uživatelsky přívětivého názvu domény (například "host.contoso.com") na číselnou internetovou adresu (například 192.168.1.1). **Resolve** vrátí <xref:System.Net.IPHostEntry> soubor obsahující seznam adres a aliasů pro požadovaný název. Ve většině případů můžete použít první adresu <xref:System.Net.IPHostEntry.AddressList%2A> vrácenou v poli. Následující kód získá <xref:System.Net.IPAddress> adresu OBSAHUJÍCÍ IP adresu pro host.contoso.com serveru.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 Úřad iana (Internet Assigned Numbers Authority) definuje čísla portů pro běžné služby (další informace naleznete v [tématu Název služby a registr čísel portů transportního protokolu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). Ostatní služby mohou mít registrovaná čísla portů v rozsahu 1 024 až 65 535. Následující kód kombinuje IP adresu pro host.contoso.com s číslem portu a vytvoří vzdálený koncový bod pro připojení.  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 Po určení adresy vzdáleného zařízení a výběru portu, který má být používán pro připojení, se aplikace může pokusit navázat spojení se vzdáleným zařízením. Následující příklad používá existující **IPEndPoint** pro připojení ke vzdálenému zařízení a zachycuje všechny výjimky, které jsou vyvolány.  
  
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
  
## <a name="see-also"></a>Viz také

- [Použití synchronního klientského soketu](using-a-synchronous-client-socket.md)
- [Použití asynchronního klientského soketu](using-an-asynchronous-client-socket.md)
- [Postupy: Vytvoření soketu](how-to-create-a-socket.md)
- [Sokety](sockets.md)
