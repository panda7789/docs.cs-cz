---
title: "Použití klienta soketů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 25c033ae46abc65040c00b6beb105c8ebb6b1d90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-client-sockets"></a>Použití klienta soketů
Před spuštěním konverzace prostřednictvím <xref:System.Net.Sockets.Socket>, je nutné vytvořit datového kanálu mezi vaší aplikací a vzdálená zařízení. I když existují další rodiny adres sítě a protokoly, tento příklad ukazuje postup vytvoření připojení TCP/IP k vzdálené služby.  
  
 TCP/IP používá síťová adresa a číslo portu služby k jednoznačné identifikaci služby. Síťová adresa identifikuje určité zařízení v síti; číslo portu identifikuje specifické služby v tomto zařízení pro připojení k. Kombinace portu síťového adresu a služby se nazývá koncový bod, který je reprezentován v rozhraní .NET Framework pomocí <xref:System.Net.EndPoint> třídy. Následníka **koncový bod** je definována pro všechny podporované rodina adres; pro rodina IP adres, je třída <xref:System.Net.IPEndPoint>.  
  
 <xref:System.Net.Dns> Třída poskytuje název domény služby pro aplikace, které používají protokol TCP/IP internetové služby. <xref:System.Net.Dns.Resolve%2A> Metoda dotazuje serveru DNS pro mapování názvu uživatelsky přívětivý domény (například "host.contoso.com") na číselné internetové adresy (jako je například 192.168.1.1). **Vyřešte** vrátí <xref:System.Net.IPHostEntry> obsahující seznam adres a aliasy pro požadovaný název. Ve většině případů můžete použít první adresu vrácenou v <xref:System.Net.IPHostEntry.AddressList%2A> pole. Následující kód získá <xref:System.Net.IPAddress> obsahující IP adresu pro host.contoso.com serveru.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 Internet Assigned Numbers Authority (Iana) definuje čísla portů pro běžné služby (pro další informace najdete v tématu www.iana.org/assignments/port-numbers). Další služby můžete zaregistrovat čísla portů v rozsahu 1 024 jednotek do 65 535. Následující kód spojuje IP adresu pro host.contoso.com se číslo portu k vytvoření vzdálený koncový bod pro připojení.  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 Po určení adresa vzdáleného zařízení a zvolením port pro připojení, můžete aplikaci pokusí navázat připojení se vzdáleným zařízením. Následující příklad používá existující **IPEndPoint** pro připojení k vzdálené zařízení a zachytí všechny výjimky, které jsou vydány.  
  
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
 [Použití synchronního klientského soketu](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)  
 [Použití asynchronního klientského soketu](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [Postupy: Vytvoření soketu](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
 [Sokety](../../../docs/framework/network-programming/sockets.md)
