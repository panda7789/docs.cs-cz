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
ms.openlocfilehash: 43e1d54d4e74b49fdf1a8997d1cc89492c9412bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117245"
---
# <a name="using-a-synchronous-server-socket"></a><span data-ttu-id="fd2e5-102">Použití synchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="fd2e5-102">Using a Synchronous Server Socket</span></span>
<span data-ttu-id="fd2e5-103">Sokety synchronního serverového pozastavit provádění aplikace, dokud obdrží požadavek na připojení soketu.</span><span class="sxs-lookup"><span data-stu-id="fd2e5-103">Synchronous server sockets suspend the execution of the application until a connection request is received on the socket.</span></span> <span data-ttu-id="fd2e5-104">Sokety synchronního serverového nejsou vhodné pro aplikace, které usnadňují použití sítě v jejich operaci, ale mohou být vhodný pro jednoduchá síť aplikace.</span><span class="sxs-lookup"><span data-stu-id="fd2e5-104">Synchronous server sockets are not suitable for applications that make heavy use of the network in their operation, but they can be suitable for simple network applications.</span></span>  
  
 <span data-ttu-id="fd2e5-105">Po <xref:System.Net.Sockets.Socket> nastavená tak, aby naslouchala na koncový bod pomocí <xref:System.Net.Sockets.Socket.Bind%2A> a <xref:System.Net.Sockets.Socket.Listen%2A> metody, je připraven tak, aby přijímal požadavky na příchozí připojení pomocí <xref:System.Net.Sockets.Socket.Accept%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="fd2e5-105">After a <xref:System.Net.Sockets.Socket> is set to listen on an endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> and <xref:System.Net.Sockets.Socket.Listen%2A> methods, it is ready to accept incoming connection requests using the <xref:System.Net.Sockets.Socket.Accept%2A> method.</span></span> <span data-ttu-id="fd2e5-106">Aplikace je pozastaveno, dokud je přijata žádost o připojení při **přijmout** metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="fd2e5-106">The application is suspended until a connection request is received when the **Accept** method is called.</span></span>  
  
 <span data-ttu-id="fd2e5-107">Při přijetí požadavku na připojení **přijmout** vrátí nový **soketu** instanci, která souvisí s připojujícího se klienta.</span><span class="sxs-lookup"><span data-stu-id="fd2e5-107">When a connection request is received, **Accept** returns a new **Socket** instance that is associated with the connecting client.</span></span> <span data-ttu-id="fd2e5-108">Následující příklad čte data z klienta, zobrazí se v konzole a vypisuje data zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="fd2e5-108">The following example reads data from the client, displays it on the console, and echoes the data back to the client.</span></span> <span data-ttu-id="fd2e5-109">**Soketu** neurčuje libovolného protokolu pro zasílání zpráv, tedy řetězec "\<EOF >" označuje konec data zprávy.</span><span class="sxs-lookup"><span data-stu-id="fd2e5-109">The **Socket** does not specify any messaging protocol, so the string "\<EOF>" marks the end of the message data.</span></span> <span data-ttu-id="fd2e5-110">Předpokládá, že **soketu** s názvem `listener` byl inicializován a vázán na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="fd2e5-110">It assumes that a **Socket** named `listener` has been initialized and bound to an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fd2e5-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd2e5-111">See also</span></span>

- [<span data-ttu-id="fd2e5-112">Použití asynchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="fd2e5-112">Using an Asynchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="fd2e5-113">Příklad synchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="fd2e5-113">Synchronous Server Socket Example</span></span>](../../../docs/framework/network-programming/synchronous-server-socket-example.md)
- [<span data-ttu-id="fd2e5-114">Naslouchání pomocí soketů</span><span class="sxs-lookup"><span data-stu-id="fd2e5-114">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
