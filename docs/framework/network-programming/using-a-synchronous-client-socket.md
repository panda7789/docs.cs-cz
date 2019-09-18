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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047077"
---
# <a name="using-a-synchronous-client-socket"></a>Použití synchronního klientského soketu
Synchronní soket klienta pozastaví program aplikace a operace sítě se dokončí. Synchronní sokety nejsou vhodné pro aplikace, které pro svou práci využívají těžké sítě, ale můžou povolit jednoduchý přístup k síťovým službám pro jiné aplikace.  
  
 Chcete-li odeslat data, předejte pole bajtů do jedné <xref:System.Net.Sockets.Socket> z metod odeslání dat třídy (<xref:System.Net.Sockets.Socket.Send%2A> a <xref:System.Net.Sockets.Socket.SendTo%2A>). Následující příklad kóduje řetězec do vyrovnávací paměti pole bajtů pomocí <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> vlastnosti a poté přenáší vyrovnávací paměť na síťové zařízení pomocí metody **Send** . Metoda **Send** vrátí počet bajtů odeslaných síťovému zařízení.  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 Metoda **Send** odstraní bajty z vyrovnávací paměti a zařadí je do fronty pomocí síťového rozhraní, které se odešle síťovému zařízení. Síťové rozhraní pravděpodobně data neodesílá okamžitě, ale pošle je, pokud je připojení normálně <xref:System.Net.Sockets.Socket.Shutdown%2A> ukončené metodou.  
  
 Pokud chcete přijímat data ze síťového zařízení, předejte vyrovnávací paměť jedné z metod Receive- **data třídy** DataClass (<xref:System.Net.Sockets.Socket.Receive%2A> a <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>). Synchronní sokety aplikaci pozastaví, dokud nejsou bajty přijímány ze sítě nebo dokud není soket uzavřen. Následující příklad přijímá data ze sítě a poté je zobrazuje v konzole nástroje. V příkladu se předpokládá, že data přicházející ze sítě jsou text s kódováním ASCII. Metoda **Receive** vrátí počet bajtů přijatých ze sítě.  
  
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
  
 V případě, že soket již není potřeba, je nutné jej uvolnit voláním <xref:System.Net.Sockets.Socket.Shutdown%2A> metody a následným voláním metody **Close** . Následující příklad uvolní **soket**. <xref:System.Net.Sockets.SocketShutdown> Výčet definuje konstanty, které určují, zda má být soket uzavřen pro odesílání, pro příjem nebo pro obojí.  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a>Viz také:

- [Použití asynchronního klientského soketu](using-an-asynchronous-client-socket.md)
- [Naslouchání pomocí soketů](listening-with-sockets.md)
- [Příklad synchronního klientského soketu](synchronous-client-socket-example.md)
