---
title: Použití klientských soketů
description: Tento příklad ukazuje, jak vytvořit připojení TCP/IP ke vzdálené službě pomocí soketu v .NET Framework.
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
ms.openlocfilehash: 1dc02d0b3651d5766d1d30752566217d8417af0c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501999"
---
# <a name="using-client-sockets"></a>Použití klientských soketů
Předtím, než můžete zahájit konverzaci pomocí <xref:System.Net.Sockets.Socket> , je nutné vytvořit datový kanál mezi vaší aplikací a vzdáleným zařízením. I když existují jiné řady síťových adres a protokoly, tento příklad ukazuje, jak vytvořit připojení TCP/IP ke vzdálené službě.  
  
 Protokol TCP/IP používá k jednoznačné identifikaci služby síťovou adresu a číslo portu služby. Síťová adresa identifikuje konkrétní zařízení v síti. číslo portu identifikuje konkrétní službu, ke které se má toto zařízení připojit. Kombinace síťové adresy a portu služby se nazývá koncový bod, který je reprezentován v .NET Framework <xref:System.Net.EndPoint> třídy. Pro každou podporovanou rodinu adres je definován následník **koncového bodu** . pro rodinu IP adres je třída <xref:System.Net.IPEndPoint> .  
  
 <xref:System.Net.Dns>Třída poskytuje služby názvu domény aplikacím, které používají internetové služby TCP/IP. <xref:System.Net.Dns.Resolve%2A>Metoda se dotazuje serveru DNS na mapování uživatelsky přívětivého názvu domény (například "host.contoso.com") na číselnou internetovou adresu (například 192.168.1.1). Funkce **Resolve** vrátí <xref:System.Net.IPHostEntry> , která obsahuje seznam adres a aliasů pro požadovaný název. Ve většině případů můžete použít první adresu vrácenou v <xref:System.Net.IPHostEntry.AddressList%2A> poli. Následující kód získá <xref:System.Net.IPAddress> adresu obsahující IP adresu pro server Host.contoso.com.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 Internet Assigned Numbers Authority (IANA) definuje čísla portů pro běžné služby (Další informace najdete v části [Service Name and Transport Protocol Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). Jiné služby můžou mít registrovaná čísla portů v rozsahu 1 024 až 65 535. Následující kód kombinuje IP adresu pro host.contoso.com s číslem portu pro vytvoření vzdáleného koncového bodu pro připojení.  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 Po určení adresy vzdáleného zařízení a výběru portu, který se má použít pro připojení, se aplikace může pokusit připojit ke vzdálenému zařízení. Následující příklad používá existující **IPEndPoint** pro připojení ke vzdálenému zařízení a zachycuje všechny výjimky, které jsou vyvolány.  
  
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

- [Použití synchronního klientského soketu](using-a-synchronous-client-socket.md)
- [Použití asynchronního klientského soketu](using-an-asynchronous-client-socket.md)
- [Postupy: Vytvoření soketu](how-to-create-a-socket.md)
- [Sokety](sockets.md)
