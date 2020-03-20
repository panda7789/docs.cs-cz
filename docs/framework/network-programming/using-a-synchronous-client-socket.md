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
ms.openlocfilehash: fdecd18dc5975cd469e49de0eb0b55081e738cd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047077"
---
# <a name="using-a-synchronous-client-socket"></a>Použití synchronního klientského soketu
Synchronní klientský soket pozastaví aplikační program po dokončení síťové operace. Synchronní sokety nejsou vhodné pro aplikace, které využívají síť pro jejich provoz, ale mohou umožnit jednoduchý přístup k síťovým službám pro jiné aplikace.  
  
 Chcete-li odeslat data, přejděte <xref:System.Net.Sockets.Socket> bajtové pole do<xref:System.Net.Sockets.Socket.Send%2A> jedné <xref:System.Net.Sockets.Socket.SendTo%2A>z metod odesílání dat třídy ( a ). Následující příklad kóduje řetězec do vyrovnávací paměti <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> bajtového pole pomocí vlastnosti a poté přenáší vyrovnávací paměť do síťového zařízení pomocí metody **Send.** Metoda **Send** vrátí počet bajtů odeslaných do síťového zařízení.  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 Send **Send** Metoda odebere bajty z vyrovnávací paměti a fronty je se síťovým rozhraním, které mají být odeslány do síťového zařízení. Síťové rozhraní nemusí odeslat data okamžitě, ale nakonec je odešle, pokud je <xref:System.Net.Sockets.Socket.Shutdown%2A> připojení normálně uzavřeno metodou.  
  
 Chcete-li přijímat data ze síťového zařízení, předejte vyrovnávací paměť jedné<xref:System.Net.Sockets.Socket.Receive%2A> <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>z metod přijímat data třídy **Socket** ( a ). Synchronní sokety pozastaví aplikaci, dokud bajty jsou přijaty ze sítě nebo dokud soket je uzavřen. Následující příklad přijímá data ze sítě a potom je zobrazí v konzole. Příklad předpokládá, že data přicházející ze sítě je ascii kódovaný text. Metoda **Receive** vrátí počet bajtů přijatých ze sítě.  
  
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
  
 Pokud soket již není potřeba, je třeba <xref:System.Net.Sockets.Socket.Shutdown%2A> jej uvolnit voláním metody a **voláním** Close metody. Následující příklad uvolní **Socket**. Výčet <xref:System.Net.Sockets.SocketShutdown> definuje konstanty, které označují, zda má být soket uzavřen pro odesílání, pro příjem nebo pro obojí.  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a>Viz také

- [Použití asynchronního klientského soketu](using-an-asynchronous-client-socket.md)
- [Naslouchání pomocí soketů](listening-with-sockets.md)
- [Příklad synchronního klientského soketu](synchronous-client-socket-example.md)
