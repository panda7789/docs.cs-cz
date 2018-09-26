---
title: Použití synchronního serverového soketu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- synchronous server sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- server sockets
- receiving data, sockets
- Socket class, synchronous server sockets
- protocols, sockets
- sockets, synchronous server sockets
- Internet, sockets
ms.assetid: d1ce882e-653e-41f5-9289-844ec855b804
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 2e79c9a75e4513be91af1104195af3614b49092d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47176487"
---
# <a name="using-a-synchronous-server-socket"></a>Použití synchronního serverového soketu
Sokety synchronního serverového pozastavit provádění aplikace, dokud obdrží požadavek na připojení soketu. Sokety synchronního serverového nejsou vhodné pro aplikace, které usnadňují použití sítě v jejich operaci, ale mohou být vhodný pro jednoduchá síť aplikace.  
  
 Po <xref:System.Net.Sockets.Socket> nastavená tak, aby naslouchala na koncový bod pomocí <xref:System.Net.Sockets.Socket.Bind%2A> a <xref:System.Net.Sockets.Socket.Listen%2A> metody, je připraven tak, aby přijímal požadavky na příchozí připojení pomocí <xref:System.Net.Sockets.Socket.Accept%2A> metody. Aplikace je pozastaveno, dokud je přijata žádost o připojení při **přijmout** metoda je volána.  
  
 Při přijetí požadavku na připojení **přijmout** vrátí nový **soketu** instanci, která souvisí s připojujícího se klienta. Následující příklad čte data z klienta, zobrazí se v konzole a vypisuje data zpět do klienta. **Soketu** neurčuje libovolného protokolu pro zasílání zpráv, tedy řetězec "\<EOF >" označuje konec data zprávy. Předpokládá, že **soketu** s názvem `listener` byl inicializován a vázán na koncový bod.  
  
```vb  
Console.WriteLine("Waiting for a connection...")  
Dim handler As Socket = listener.Accept()  
Dim data As String = Nothing  
  
While True  
    bytes = New Byte(1024) {}  
    Dim bytesRec As Integer = handler.Receive(bytes)  
    data += Encoding.ASCII.GetString(bytes, 0, bytesRec)  
    If data.IndexOf("<EOF>") > - 1 Then  
        Exit While  
    End If  
End While  
  
Console.WriteLine("Text received : {0}", data)  
  
Dim msg As Byte() = Encoding.ASCII.GetBytes(data)  
handler.Send(msg)  
handler.Shutdown(SocketShutdown.Both)  
handler.Close()  
```  
  
```csharp  
Console.WriteLine("Waiting for a connection...");  
Socket handler = listener.Accept();  
String data = null;  
  
while (true) {  
    bytes = new byte[1024];  
    int bytesRec = handler.Receive(bytes);  
    data += Encoding.ASCII.GetString(bytes,0,bytesRec);  
    if (data.IndexOf("<EOF>") > -1) {  
        break;  
    }  
}  
  
Console.WriteLine( "Text received : {0}", data);  
  
byte[] msg = Encoding.ASCII.GetBytes(data);  
handler.Send(msg);  
handler.Shutdown(SocketShutdown.Both);  
handler.Close();  
```  
  
## <a name="see-also"></a>Viz také  
 [Použití asynchronního serverového soketu](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [Příklad synchronního serverového soketu](../../../docs/framework/network-programming/synchronous-server-socket-example.md)  
 [Naslouchání pomocí soketů](../../../docs/framework/network-programming/listening-with-sockets.md)
