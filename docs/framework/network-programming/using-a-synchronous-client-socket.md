---
title: Pomocí soket synchronního klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- synchronous client sockets
- Socket class, synchronous client sockets
- receiving data, sockets
- sockets, synchronous client sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: 945d00c6-7202-466c-9df9-140b84156d43
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c9101957c6c4b9961ca5985bda8b8f82d69b45d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-a-synchronous-client-socket"></a>Pomocí soket synchronního klienta
Soket synchronního klienta pozastaví programu aplikace při dokončení operace sítě. Synchronní sockets nejsou vhodné pro aplikace, které hodně využívají sítě pro jejich operaci, ale umožňují jednoduchý přístup k síťové služby pro jiné aplikace.  
  
 K odesílání dat, předejte do jednoho z bajtového pole <xref:System.Net.Sockets.Socket> metody třídy odeslání dat (<xref:System.Net.Sockets.Socket.Send%2A> a <xref:System.Net.Sockets.Socket.SendTo%2A>). V následujícím příkladu kóduje řetězce na bajtové pole vyrovnávací paměti pomocí <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> vlastnost a potom odesílá vyrovnávací paměť k síti pomocí zařízení **odeslat** metoda. **Odeslat** metoda vrátí počet bajtů odeslaných síťové zařízení.  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 **Odeslat** metoda odebere bajtů z vyrovnávací paměti a fronty je se síťovým rozhraním k odeslání do síťového zařízení. Síťové rozhraní nemusí posílat data okamžitě, ale odešle ho nakonec tak dlouho, dokud připojení je ukončeno, obvykle s <xref:System.Net.Sockets.Socket.Shutdown%2A> metoda.  
  
 Pro příjem dat ze síťového zařízení, předat do jednoho z vyrovnávací paměti **soketu** metody třídy přijímat data (<xref:System.Net.Sockets.Socket.Receive%2A> a <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>). Synchronní sockets bude aplikace pozastavit, dokud se přijaté bajty ze sítě, nebo dokud nezavře soketu. V následujícím příkladu přijímá data ze sítě a potom zobrazí v konzole. Příklad předpokládá, že dat pocházejících z sítě je kódováním ASCII text. **Receive** metoda vrátí počet bajtů přijatých ze sítě.  
  
```vb  
Dim bytes(1024) As Byte  
Dim bytesRec = s.Receive(bytes)  
Console.WriteLine("Echoed text = {0}", _  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec))  
```  
  
```csharp  
byte[] bytes = new byte[1024];  
int bytesRec = s.Receive(bytes);  
Console.WriteLine("Echoed text = {0}",  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec));  
```  
  
 Až soketu se už nepotřebuje, budete muset verze voláním <xref:System.Net.Sockets.Socket.Shutdown%2A> metoda a pak volání **Zavřít** metoda. Následující příklad uvolní **soketu**. <xref:System.Net.Sockets.SocketShutdown> Výčet definuje konstanty, které označuje, zda by měly být ukončeny soket pro odesílání, pro příjem nebo pro obojí.  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a>Viz také  
 [Použití asynchronního klientského soketu](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [Naslouchání pomocí soketů](../../../docs/framework/network-programming/listening-with-sockets.md)  
 [Příklad synchronního klientského soketu](../../../docs/framework/network-programming/synchronous-client-socket-example.md)
