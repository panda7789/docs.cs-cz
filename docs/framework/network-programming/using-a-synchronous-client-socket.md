---
title: Použití synchronního klientského soketu
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
ms.openlocfilehash: a368048f83540bf5bb9cd43a0a88c40641eb7e94
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621695"
---
# <a name="using-a-synchronous-client-socket"></a>Použití synchronního klientského soketu
Synchronního klientského soketu pozastaví program aplikace, zatímco se dokončují síťové operace. Synchronní sockets nejsou vhodné pro aplikace, které se hojně používají síť pro jejich operaci, ale umožňují snadný přístup k síťovým službám pro jiné aplikace.  
  
 K odesílání dat, předat do jedné z bajtového pole <xref:System.Net.Sockets.Socket> metody třídy odesílání dat (<xref:System.Net.Sockets.Socket.Send%2A> a <xref:System.Net.Sockets.Socket.SendTo%2A>). V následujícím příkladu kóduje řetězec na bajtové pole vyrovnávací paměti pomocí <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> vlastnost a potom odesílá vyrovnávací paměti k síti pomocí zařízení **odeslat** metody. **Odeslat** metoda vrátí počet bajtů odeslaných k síťovému zařízení.  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 **Odeslat** metoda odebere počet bajtů z vyrovnávací paměti a je zařadí do fronty se síťovým rozhraním odesílání k síťovému zařízení. Síťové rozhraní nemusí posílat data okamžitě, ale tak dlouho, dokud se připojení uzavře obvykle se to se odešle nakonec <xref:System.Net.Sockets.Socket.Shutdown%2A> metody.  
  
 Pro příjem dat ze síťového zařízení, předejte do jednoho z vyrovnávací paměti **soketu** metody třídy přijímat data (<xref:System.Net.Sockets.Socket.Receive%2A> a <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>). Synchronní sockets bude aplikace pozastavit, dokud přijímání bajtů ze sítě nebo dokud není zavřena soketu. Následující příklad přijímá data ze sítě a pak jej zobrazí v konzole. Tento příklad předpokládá, že dat pocházejících ze sítě je text v kódování ASCII. **Receive** metoda vrátí počet bajtů přijatých ze sítě.  
  
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
  
 Když soket je už nepotřebujete, budete muset uvolnit voláním <xref:System.Net.Sockets.Socket.Shutdown%2A> metoda a následným voláním **Zavřít** metody. V následujícím příkladu se uvolní **soketu**. <xref:System.Net.Sockets.SocketShutdown> Výčet definuje konstanty, které označuje, zda by měly být uzavřeny soket pro odesílání, pro příjem nebo oba systémy.  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a>Viz také:
- [Použití asynchronního klientského soketu](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)
- [Naslouchání pomocí soketů](../../../docs/framework/network-programming/listening-with-sockets.md)
- [Příklad synchronního klientského soketu](../../../docs/framework/network-programming/synchronous-client-socket-example.md)
