---
title: Pomocí soket synchronního serveru
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
manager: markl
ms.openlocfilehash: 4f04255edf9533612dd6b0733331fb18587ff3f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-a-synchronous-server-socket"></a>Pomocí soket synchronního serveru
Synchronní serveru sockets pozastavit provádění aplikace, dokud obdrží žádost o připojení soketu. Sokety synchronní serveru nejsou vhodné pro aplikace, které hodně využívají sítě v jejich operaci, ale mohou být vhodný pro jednoduché síťových aplikací.  
  
 Po <xref:System.Net.Sockets.Socket> je nastaven tak, aby naslouchala na k koncový bod pomocí <xref:System.Net.Sockets.Socket.Bind%2A> a <xref:System.Net.Sockets.Socket.Listen%2A> metody, je připravena přijímat požadavky na příchozí připojení pomocí <xref:System.Net.Sockets.Socket.Accept%2A> metoda. Aplikace je pozastaveno, dokud je přijal žádost o připojení při **přijmout** metoda je volána.  
  
 Po přijetí požadavku na připojení **přijmout** vrátí novou **soketu** instance, který je přidružen připojujícího se klienta. Následující příklad načte data z klienta, zobrazí v konzole a vrátí data zpět do klienta. **Soketu** neurčuje libovolný protokol pro zasílání zpráv, takže řetězec "\<EOF >" označuje konec daty zprávy. Předpokládá, že **soketu** s názvem `listener` byl inicializován a vázána na koncový bod.  
  
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
