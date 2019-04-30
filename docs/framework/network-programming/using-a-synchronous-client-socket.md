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
ms.openlocfilehash: 339f9c9d8b25f6deef4cc77f60c26b7b5d017ce0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796939"
---
# <a name="using-a-synchronous-client-socket"></a><span data-ttu-id="1c85e-102">Použití synchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="1c85e-102">Using a Synchronous Client Socket</span></span>
<span data-ttu-id="1c85e-103">Synchronního klientského soketu pozastaví program aplikace, zatímco se dokončují síťové operace.</span><span class="sxs-lookup"><span data-stu-id="1c85e-103">A synchronous client socket suspends the application program while the network operation completes.</span></span> <span data-ttu-id="1c85e-104">Synchronní sockets nejsou vhodné pro aplikace, které se hojně používají síť pro jejich operaci, ale umožňují snadný přístup k síťovým službám pro jiné aplikace.</span><span class="sxs-lookup"><span data-stu-id="1c85e-104">Synchronous sockets are not suitable for applications that make heavy use of the network for their operation, but they can enable simple access to network services for other applications.</span></span>  
  
 <span data-ttu-id="1c85e-105">K odesílání dat, předat do jedné z bajtového pole <xref:System.Net.Sockets.Socket> metody třídy odesílání dat (<xref:System.Net.Sockets.Socket.Send%2A> a <xref:System.Net.Sockets.Socket.SendTo%2A>).</span><span class="sxs-lookup"><span data-stu-id="1c85e-105">To send data, pass a byte array to one of the <xref:System.Net.Sockets.Socket> class's send-data methods (<xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.SendTo%2A>).</span></span> <span data-ttu-id="1c85e-106">V následujícím příkladu kóduje řetězec na bajtové pole vyrovnávací paměti pomocí <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> vlastnost a potom odesílá vyrovnávací paměti k síti pomocí zařízení **odeslat** metody.</span><span class="sxs-lookup"><span data-stu-id="1c85e-106">The following example encodes a string into a byte array buffer using the <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> property and then transmits the buffer to the network device using the **Send** method.</span></span> <span data-ttu-id="1c85e-107">**Odeslat** metoda vrátí počet bajtů odeslaných k síťovému zařízení.</span><span class="sxs-lookup"><span data-stu-id="1c85e-107">The **Send** method returns the number of bytes sent to the network device.</span></span>  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 <span data-ttu-id="1c85e-108">**Odeslat** metoda odebere počet bajtů z vyrovnávací paměti a je zařadí do fronty se síťovým rozhraním odesílání k síťovému zařízení.</span><span class="sxs-lookup"><span data-stu-id="1c85e-108">The **Send** method removes the bytes from the buffer and queues them with the network interface to be sent to the network device.</span></span> <span data-ttu-id="1c85e-109">Síťové rozhraní nemusí posílat data okamžitě, ale tak dlouho, dokud se připojení uzavře obvykle se to se odešle nakonec <xref:System.Net.Sockets.Socket.Shutdown%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1c85e-109">The network interface might not send the data immediately, but it will send it eventually, as long as the connection is closed normally with the <xref:System.Net.Sockets.Socket.Shutdown%2A> method.</span></span>  
  
 <span data-ttu-id="1c85e-110">Pro příjem dat ze síťového zařízení, předejte do jednoho z vyrovnávací paměti **soketu** metody třídy přijímat data (<xref:System.Net.Sockets.Socket.Receive%2A> a <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>).</span><span class="sxs-lookup"><span data-stu-id="1c85e-110">To receive data from a network device, pass a buffer to one of the **Socket** class's receive-data methods (<xref:System.Net.Sockets.Socket.Receive%2A> and <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>).</span></span> <span data-ttu-id="1c85e-111">Synchronní sockets bude aplikace pozastavit, dokud přijímání bajtů ze sítě nebo dokud není zavřena soketu.</span><span class="sxs-lookup"><span data-stu-id="1c85e-111">Synchronous sockets will suspend the application until bytes are received from the network or until the socket is closed.</span></span> <span data-ttu-id="1c85e-112">Následující příklad přijímá data ze sítě a pak jej zobrazí v konzole.</span><span class="sxs-lookup"><span data-stu-id="1c85e-112">The following example receives data from the network and then displays it on the console.</span></span> <span data-ttu-id="1c85e-113">Tento příklad předpokládá, že dat pocházejících ze sítě je text v kódování ASCII.</span><span class="sxs-lookup"><span data-stu-id="1c85e-113">The example assumes that the data coming from the network is ASCII-encoded text.</span></span> <span data-ttu-id="1c85e-114">**Receive** metoda vrátí počet bajtů přijatých ze sítě.</span><span class="sxs-lookup"><span data-stu-id="1c85e-114">The **Receive** method returns the number of bytes received from the network.</span></span>  
  
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
  
 <span data-ttu-id="1c85e-115">Když soket je už nepotřebujete, budete muset uvolnit voláním <xref:System.Net.Sockets.Socket.Shutdown%2A> metoda a následným voláním **Zavřít** metody.</span><span class="sxs-lookup"><span data-stu-id="1c85e-115">When the socket is no longer needed, you need to release it by calling the <xref:System.Net.Sockets.Socket.Shutdown%2A> method and then calling the **Close** method.</span></span> <span data-ttu-id="1c85e-116">V následujícím příkladu se uvolní **soketu**.</span><span class="sxs-lookup"><span data-stu-id="1c85e-116">The following example releases a **Socket**.</span></span> <span data-ttu-id="1c85e-117"><xref:System.Net.Sockets.SocketShutdown> Výčet definuje konstanty, které označuje, zda by měly být uzavřeny soket pro odesílání, pro příjem nebo oba systémy.</span><span class="sxs-lookup"><span data-stu-id="1c85e-117">The <xref:System.Net.Sockets.SocketShutdown> enumeration defines constants that indicate whether the socket should be closed for sending, for receiving, or for both.</span></span>  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="1c85e-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c85e-118">See also</span></span>

- [<span data-ttu-id="1c85e-119">Použití asynchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="1c85e-119">Using an Asynchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="1c85e-120">Naslouchání pomocí soketů</span><span class="sxs-lookup"><span data-stu-id="1c85e-120">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
- [<span data-ttu-id="1c85e-121">Příklad synchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="1c85e-121">Synchronous Client Socket Example</span></span>](../../../docs/framework/network-programming/synchronous-client-socket-example.md)
