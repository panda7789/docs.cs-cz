---
title: "Pomocí soket synchronního klienta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 03595539d825f26251a24fce33ede2552b79b38b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-a-synchronous-client-socket"></a><span data-ttu-id="79008-102">Pomocí soket synchronního klienta</span><span class="sxs-lookup"><span data-stu-id="79008-102">Using a Synchronous Client Socket</span></span>
<span data-ttu-id="79008-103">Soket synchronního klienta pozastaví programu aplikace při dokončení operace sítě.</span><span class="sxs-lookup"><span data-stu-id="79008-103">A synchronous client socket suspends the application program while the network operation completes.</span></span> <span data-ttu-id="79008-104">Synchronní sockets nejsou vhodné pro aplikace, které hodně využívají sítě pro jejich operaci, ale umožňují jednoduchý přístup k síťové služby pro jiné aplikace.</span><span class="sxs-lookup"><span data-stu-id="79008-104">Synchronous sockets are not suitable for applications that make heavy use of the network for their operation, but they can enable simple access to network services for other applications.</span></span>  
  
 <span data-ttu-id="79008-105">K odesílání dat, předejte do jednoho z bajtového pole <xref:System.Net.Sockets.Socket> metody třídy odeslání dat (<xref:System.Net.Sockets.Socket.Send%2A> a <xref:System.Net.Sockets.Socket.SendTo%2A>).</span><span class="sxs-lookup"><span data-stu-id="79008-105">To send data, pass a byte array to one of the <xref:System.Net.Sockets.Socket> class's send-data methods (<xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.SendTo%2A>).</span></span> <span data-ttu-id="79008-106">V následujícím příkladu kóduje řetězce na bajtové pole vyrovnávací paměti pomocí <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> vlastnost a potom odesílá vyrovnávací paměť k síti pomocí zařízení **odeslat** metoda.</span><span class="sxs-lookup"><span data-stu-id="79008-106">The following example encodes a string into a byte array buffer using the <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> property and then transmits the buffer to the network device using the **Send** method.</span></span> <span data-ttu-id="79008-107">**Odeslat** metoda vrátí počet bajtů odeslaných síťové zařízení.</span><span class="sxs-lookup"><span data-stu-id="79008-107">The **Send** method returns the number of bytes sent to the network device.</span></span>  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 <span data-ttu-id="79008-108">**Odeslat** metoda odebere bajtů z vyrovnávací paměti a fronty je se síťovým rozhraním k odeslání do síťového zařízení.</span><span class="sxs-lookup"><span data-stu-id="79008-108">The **Send** method removes the bytes from the buffer and queues them with the network interface to be sent to the network device.</span></span> <span data-ttu-id="79008-109">Síťové rozhraní nemusí posílat data okamžitě, ale odešle ho nakonec tak dlouho, dokud připojení je ukončeno, obvykle s <xref:System.Net.Sockets.Socket.Shutdown%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="79008-109">The network interface might not send the data immediately, but it will send it eventually, as long as the connection is closed normally with the <xref:System.Net.Sockets.Socket.Shutdown%2A> method.</span></span>  
  
 <span data-ttu-id="79008-110">Pro příjem dat ze síťového zařízení, předat do jednoho z vyrovnávací paměti **soketu** metody třídy přijímat data (<xref:System.Net.Sockets.Socket.Receive%2A> a <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>).</span><span class="sxs-lookup"><span data-stu-id="79008-110">To receive data from a network device, pass a buffer to one of the **Socket** class's receive-data methods (<xref:System.Net.Sockets.Socket.Receive%2A> and <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>).</span></span> <span data-ttu-id="79008-111">Synchronní sockets bude aplikace pozastavit, dokud se přijaté bajty ze sítě, nebo dokud nezavře soketu.</span><span class="sxs-lookup"><span data-stu-id="79008-111">Synchronous sockets will suspend the application until bytes are received from the network or until the socket is closed.</span></span> <span data-ttu-id="79008-112">V následujícím příkladu přijímá data ze sítě a potom zobrazí v konzole.</span><span class="sxs-lookup"><span data-stu-id="79008-112">The following example receives data from the network and then displays it on the console.</span></span> <span data-ttu-id="79008-113">Příklad předpokládá, že dat pocházejících z sítě je kódováním ASCII text.</span><span class="sxs-lookup"><span data-stu-id="79008-113">The example assumes that the data coming from the network is ASCII-encoded text.</span></span> <span data-ttu-id="79008-114">**Receive** metoda vrátí počet bajtů přijatých ze sítě.</span><span class="sxs-lookup"><span data-stu-id="79008-114">The **Receive** method returns the number of bytes received from the network.</span></span>  
  
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
  
 <span data-ttu-id="79008-115">Až soketu se už nepotřebuje, budete muset verze voláním <xref:System.Net.Sockets.Socket.Shutdown%2A> metoda a pak volání **Zavřít** metoda.</span><span class="sxs-lookup"><span data-stu-id="79008-115">When the socket is no longer needed, you need to release it by calling the <xref:System.Net.Sockets.Socket.Shutdown%2A> method and then calling the **Close** method.</span></span> <span data-ttu-id="79008-116">Následující příklad uvolní **soketu**.</span><span class="sxs-lookup"><span data-stu-id="79008-116">The following example releases a **Socket**.</span></span> <span data-ttu-id="79008-117"><xref:System.Net.Sockets.SocketShutdown> Výčet definuje konstanty, které označuje, zda by měly být ukončeny soket pro odesílání, pro příjem nebo pro obojí.</span><span class="sxs-lookup"><span data-stu-id="79008-117">The <xref:System.Net.Sockets.SocketShutdown> enumeration defines constants that indicate whether the socket should be closed for sending, for receiving, or for both.</span></span>  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="79008-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="79008-118">See Also</span></span>  
 [<span data-ttu-id="79008-119">Použití asynchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="79008-119">Using an Asynchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [<span data-ttu-id="79008-120">Naslouchání pomocí soketů</span><span class="sxs-lookup"><span data-stu-id="79008-120">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)  
 [<span data-ttu-id="79008-121">Příklad synchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="79008-121">Synchronous Client Socket Example</span></span>](../../../docs/framework/network-programming/synchronous-client-socket-example.md)
