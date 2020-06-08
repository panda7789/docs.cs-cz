---
title: Použití synchronního serverového soketu
description: Tento příklad ukazuje synchronní server soketu v .NET Framework, který pozastaví aplikaci, dokud nebude přijata žádost o připojení na soketu.
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
ms.openlocfilehash: 9e7d32595f554b32ecc72bbb1f1a469ad5935467
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502051"
---
# <a name="using-a-synchronous-server-socket"></a>Použití synchronního serverového soketu
Synchronní sokety serveru pozastaví provádění aplikace, dokud se na soketu nepřijme požadavek na připojení. Synchronní sokety serveru nejsou vhodné pro aplikace, které při jejich provozu využívají těžké sítě, ale můžou být vhodné pro jednoduché síťové aplikace.  
  
 Jakmile <xref:System.Net.Sockets.Socket> je nastaveno naslouchání na koncovém bodu pomocí <xref:System.Net.Sockets.Socket.Bind%2A> metod a <xref:System.Net.Sockets.Socket.Listen%2A> , je připraven přijímat příchozí požadavky na připojení pomocí <xref:System.Net.Sockets.Socket.Accept%2A> metody. Aplikace je pozastavena, dokud nebude přijata žádost o připojení při volání metody **Accept** .  
  
 Po přijetí žádosti o připojení vrátí funkce **Accept** novou instanci **soketu** , která je přidružená k připojujícímu se klientovi. Následující příklad čte data z klienta, zobrazuje je v konzole nástroje a vrací data zpět klientovi. **Soket** neurčuje žádný protokol zasílání zpráv, takže řetězec " \<EOF> " označuje konec dat zprávy. Předpokládá, že **soket** s názvem `listener` byl inicializován a svázán s koncovým bodem.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Použití asynchronního serverového soketu](using-an-asynchronous-server-socket.md)
- [Příklad synchronního serverového soketu](synchronous-server-socket-example.md)
- [Naslouchání pomocí soketů](listening-with-sockets.md)
