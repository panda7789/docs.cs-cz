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
# <a name="using-a-synchronous-client-socket"></a><span data-ttu-id="9df37-102">Použití synchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="9df37-102">Using a Synchronous Client Socket</span></span>
<span data-ttu-id="9df37-103">Synchronní klientský soket pozastaví aplikační program po dokončení síťové operace.</span><span class="sxs-lookup"><span data-stu-id="9df37-103">A synchronous client socket suspends the application program while the network operation completes.</span></span> <span data-ttu-id="9df37-104">Synchronní sokety nejsou vhodné pro aplikace, které využívají síť pro jejich provoz, ale mohou umožnit jednoduchý přístup k síťovým službám pro jiné aplikace.</span><span class="sxs-lookup"><span data-stu-id="9df37-104">Synchronous sockets are not suitable for applications that make heavy use of the network for their operation, but they can enable simple access to network services for other applications.</span></span>  
  
 <span data-ttu-id="9df37-105">Chcete-li odeslat data, přejděte <xref:System.Net.Sockets.Socket> bajtové pole do<xref:System.Net.Sockets.Socket.Send%2A> jedné <xref:System.Net.Sockets.Socket.SendTo%2A>z metod odesílání dat třídy ( a ).</span><span class="sxs-lookup"><span data-stu-id="9df37-105">To send data, pass a byte array to one of the <xref:System.Net.Sockets.Socket> class's send-data methods (<xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.SendTo%2A>).</span></span> <span data-ttu-id="9df37-106">Následující příklad kóduje řetězec do vyrovnávací paměti <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> bajtového pole pomocí vlastnosti a poté přenáší vyrovnávací paměť do síťového zařízení pomocí metody **Send.**</span><span class="sxs-lookup"><span data-stu-id="9df37-106">The following example encodes a string into a byte array buffer using the <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> property and then transmits the buffer to the network device using the **Send** method.</span></span> <span data-ttu-id="9df37-107">Metoda **Send** vrátí počet bajtů odeslaných do síťového zařízení.</span><span class="sxs-lookup"><span data-stu-id="9df37-107">The **Send** method returns the number of bytes sent to the network device.</span></span>  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 <span data-ttu-id="9df37-108">Send **Send** Metoda odebere bajty z vyrovnávací paměti a fronty je se síťovým rozhraním, které mají být odeslány do síťového zařízení.</span><span class="sxs-lookup"><span data-stu-id="9df37-108">The **Send** method removes the bytes from the buffer and queues them with the network interface to be sent to the network device.</span></span> <span data-ttu-id="9df37-109">Síťové rozhraní nemusí odeslat data okamžitě, ale nakonec je odešle, pokud je <xref:System.Net.Sockets.Socket.Shutdown%2A> připojení normálně uzavřeno metodou.</span><span class="sxs-lookup"><span data-stu-id="9df37-109">The network interface might not send the data immediately, but it will send it eventually, as long as the connection is closed normally with the <xref:System.Net.Sockets.Socket.Shutdown%2A> method.</span></span>  
  
 <span data-ttu-id="9df37-110">Chcete-li přijímat data ze síťového zařízení, předejte vyrovnávací paměť jedné<xref:System.Net.Sockets.Socket.Receive%2A> <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>z metod přijímat data třídy **Socket** ( a ).</span><span class="sxs-lookup"><span data-stu-id="9df37-110">To receive data from a network device, pass a buffer to one of the **Socket** class's receive-data methods (<xref:System.Net.Sockets.Socket.Receive%2A> and <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>).</span></span> <span data-ttu-id="9df37-111">Synchronní sokety pozastaví aplikaci, dokud bajty jsou přijaty ze sítě nebo dokud soket je uzavřen.</span><span class="sxs-lookup"><span data-stu-id="9df37-111">Synchronous sockets will suspend the application until bytes are received from the network or until the socket is closed.</span></span> <span data-ttu-id="9df37-112">Následující příklad přijímá data ze sítě a potom je zobrazí v konzole.</span><span class="sxs-lookup"><span data-stu-id="9df37-112">The following example receives data from the network and then displays it on the console.</span></span> <span data-ttu-id="9df37-113">Příklad předpokládá, že data přicházející ze sítě je ascii kódovaný text.</span><span class="sxs-lookup"><span data-stu-id="9df37-113">The example assumes that the data coming from the network is ASCII-encoded text.</span></span> <span data-ttu-id="9df37-114">Metoda **Receive** vrátí počet bajtů přijatých ze sítě.</span><span class="sxs-lookup"><span data-stu-id="9df37-114">The **Receive** method returns the number of bytes received from the network.</span></span>  
  
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
  
 <span data-ttu-id="9df37-115">Pokud soket již není potřeba, je třeba <xref:System.Net.Sockets.Socket.Shutdown%2A> jej uvolnit voláním metody a **voláním** Close metody.</span><span class="sxs-lookup"><span data-stu-id="9df37-115">When the socket is no longer needed, you need to release it by calling the <xref:System.Net.Sockets.Socket.Shutdown%2A> method and then calling the **Close** method.</span></span> <span data-ttu-id="9df37-116">Následující příklad uvolní **Socket**.</span><span class="sxs-lookup"><span data-stu-id="9df37-116">The following example releases a **Socket**.</span></span> <span data-ttu-id="9df37-117">Výčet <xref:System.Net.Sockets.SocketShutdown> definuje konstanty, které označují, zda má být soket uzavřen pro odesílání, pro příjem nebo pro obojí.</span><span class="sxs-lookup"><span data-stu-id="9df37-117">The <xref:System.Net.Sockets.SocketShutdown> enumeration defines constants that indicate whether the socket should be closed for sending, for receiving, or for both.</span></span>  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="9df37-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="9df37-118">See also</span></span>

- [<span data-ttu-id="9df37-119">Použití asynchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="9df37-119">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="9df37-120">Naslouchání pomocí soketů</span><span class="sxs-lookup"><span data-stu-id="9df37-120">Listening with Sockets</span></span>](listening-with-sockets.md)
- [<span data-ttu-id="9df37-121">Příklad synchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="9df37-121">Synchronous Client Socket Example</span></span>](synchronous-client-socket-example.md)
