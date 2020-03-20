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
ms.openlocfilehash: cbc02c755ceefa8f31439f121a98978b82f33fa2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047037"
---
# <a name="using-a-synchronous-server-socket"></a>Použití synchronního serverového soketu
Synchronní sokety serveru pozastaví provádění aplikace, dokud není přijat požadavek na připojení v soketu. Synchronní serverové sokety nejsou vhodné pro aplikace, které při svém provozu velmi využívají síť, ale mohou být vhodné pro jednoduché síťové aplikace.  
  
 Po <xref:System.Net.Sockets.Socket> a je nastavena na naslouchání na koncovém bodu pomocí metody <xref:System.Net.Sockets.Socket.Bind%2A> a, <xref:System.Net.Sockets.Socket.Listen%2A> je připraven přijmout příchozí požadavky na připojení pomocí <xref:System.Net.Sockets.Socket.Accept%2A> metody. Aplikace je pozastavena, dokud není přijat požadavek na připojení při volání metody **Accept.**  
  
 Při přijetí požadavku na připojení **Accept** vrátí novou instanci **Socket,** která je přidružena k připojujícímu se klientovi. Následující příklad čte data z klienta, zobrazí je v konzole a ozvěny data zpět klientovi. **Socket** neurčuje žádný protokol zasílání zpráv,\<takže řetězec "EOF>" označuje konec dat zprávy. Předpokládá, že **Socket** `listener` s názvem byla inicializována a vázána na koncový bod.  
  
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

- [Použití asynchronního serverového soketu](using-an-asynchronous-server-socket.md)
- [Příklad synchronního serverového soketu](synchronous-server-socket-example.md)
- [Naslouchání pomocí soketů](listening-with-sockets.md)
