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
# <a name="using-a-synchronous-server-socket"></a><span data-ttu-id="00f9c-103">Použití synchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="00f9c-103">Using a Synchronous Server Socket</span></span>
<span data-ttu-id="00f9c-104">Synchronní sokety serveru pozastaví provádění aplikace, dokud se na soketu nepřijme požadavek na připojení.</span><span class="sxs-lookup"><span data-stu-id="00f9c-104">Synchronous server sockets suspend the execution of the application until a connection request is received on the socket.</span></span> <span data-ttu-id="00f9c-105">Synchronní sokety serveru nejsou vhodné pro aplikace, které při jejich provozu využívají těžké sítě, ale můžou být vhodné pro jednoduché síťové aplikace.</span><span class="sxs-lookup"><span data-stu-id="00f9c-105">Synchronous server sockets are not suitable for applications that make heavy use of the network in their operation, but they can be suitable for simple network applications.</span></span>  
  
 <span data-ttu-id="00f9c-106">Jakmile <xref:System.Net.Sockets.Socket> je nastaveno naslouchání na koncovém bodu pomocí <xref:System.Net.Sockets.Socket.Bind%2A> metod a <xref:System.Net.Sockets.Socket.Listen%2A> , je připraven přijímat příchozí požadavky na připojení pomocí <xref:System.Net.Sockets.Socket.Accept%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="00f9c-106">After a <xref:System.Net.Sockets.Socket> is set to listen on an endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> and <xref:System.Net.Sockets.Socket.Listen%2A> methods, it is ready to accept incoming connection requests using the <xref:System.Net.Sockets.Socket.Accept%2A> method.</span></span> <span data-ttu-id="00f9c-107">Aplikace je pozastavena, dokud nebude přijata žádost o připojení při volání metody **Accept** .</span><span class="sxs-lookup"><span data-stu-id="00f9c-107">The application is suspended until a connection request is received when the **Accept** method is called.</span></span>  
  
 <span data-ttu-id="00f9c-108">Po přijetí žádosti o připojení vrátí funkce **Accept** novou instanci **soketu** , která je přidružená k připojujícímu se klientovi.</span><span class="sxs-lookup"><span data-stu-id="00f9c-108">When a connection request is received, **Accept** returns a new **Socket** instance that is associated with the connecting client.</span></span> <span data-ttu-id="00f9c-109">Následující příklad čte data z klienta, zobrazuje je v konzole nástroje a vrací data zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="00f9c-109">The following example reads data from the client, displays it on the console, and echoes the data back to the client.</span></span> <span data-ttu-id="00f9c-110">**Soket** neurčuje žádný protokol zasílání zpráv, takže řetězec " \<EOF> " označuje konec dat zprávy.</span><span class="sxs-lookup"><span data-stu-id="00f9c-110">The **Socket** does not specify any messaging protocol, so the string "\<EOF>" marks the end of the message data.</span></span> <span data-ttu-id="00f9c-111">Předpokládá, že **soket** s názvem `listener` byl inicializován a svázán s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="00f9c-111">It assumes that a **Socket** named `listener` has been initialized and bound to an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="00f9c-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00f9c-112">See also</span></span>

- [<span data-ttu-id="00f9c-113">Použití asynchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="00f9c-113">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="00f9c-114">Příklad synchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="00f9c-114">Synchronous Server Socket Example</span></span>](synchronous-server-socket-example.md)
- [<span data-ttu-id="00f9c-115">Naslouchání pomocí soketů</span><span class="sxs-lookup"><span data-stu-id="00f9c-115">Listening with Sockets</span></span>](listening-with-sockets.md)
