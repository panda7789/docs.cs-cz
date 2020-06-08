---
title: Použití synchronního klientského soketu
description: Tento příklad ukazuje synchronní soket klienta v .NET Framework, který pozastaví program aplikace při dokončení síťové operace.
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
ms.openlocfilehash: ef682af33c10cf06ffc398c22e4a7dc1adf8290e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502064"
---
# <a name="using-a-synchronous-client-socket"></a><span data-ttu-id="04f13-103">Použití synchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="04f13-103">Using a Synchronous Client Socket</span></span>
<span data-ttu-id="04f13-104">Synchronní soket klienta pozastaví program aplikace a operace sítě se dokončí.</span><span class="sxs-lookup"><span data-stu-id="04f13-104">A synchronous client socket suspends the application program while the network operation completes.</span></span> <span data-ttu-id="04f13-105">Synchronní sokety nejsou vhodné pro aplikace, které pro svou práci využívají těžké sítě, ale můžou povolit jednoduchý přístup k síťovým službám pro jiné aplikace.</span><span class="sxs-lookup"><span data-stu-id="04f13-105">Synchronous sockets are not suitable for applications that make heavy use of the network for their operation, but they can enable simple access to network services for other applications.</span></span>  
  
 <span data-ttu-id="04f13-106">Chcete-li odeslat data, předejte pole bajtů do jedné z <xref:System.Net.Sockets.Socket> metod odeslání dat třídy ( <xref:System.Net.Sockets.Socket.Send%2A> a <xref:System.Net.Sockets.Socket.SendTo%2A> ).</span><span class="sxs-lookup"><span data-stu-id="04f13-106">To send data, pass a byte array to one of the <xref:System.Net.Sockets.Socket> class's send-data methods (<xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.SendTo%2A>).</span></span> <span data-ttu-id="04f13-107">Následující příklad kóduje řetězec do vyrovnávací paměti pole bajtů pomocí <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> vlastnosti a poté přenáší vyrovnávací paměť na síťové zařízení pomocí metody **Send** .</span><span class="sxs-lookup"><span data-stu-id="04f13-107">The following example encodes a string into a byte array buffer using the <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> property and then transmits the buffer to the network device using the **Send** method.</span></span> <span data-ttu-id="04f13-108">Metoda **Send** vrátí počet bajtů odeslaných síťovému zařízení.</span><span class="sxs-lookup"><span data-stu-id="04f13-108">The **Send** method returns the number of bytes sent to the network device.</span></span>  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 <span data-ttu-id="04f13-109">Metoda **Send** odstraní bajty z vyrovnávací paměti a zařadí je do fronty pomocí síťového rozhraní, které se odešle síťovému zařízení.</span><span class="sxs-lookup"><span data-stu-id="04f13-109">The **Send** method removes the bytes from the buffer and queues them with the network interface to be sent to the network device.</span></span> <span data-ttu-id="04f13-110">Síťové rozhraní pravděpodobně data neodesílá okamžitě, ale pošle je, pokud je připojení normálně ukončené <xref:System.Net.Sockets.Socket.Shutdown%2A> metodou.</span><span class="sxs-lookup"><span data-stu-id="04f13-110">The network interface might not send the data immediately, but it will send it eventually, as long as the connection is closed normally with the <xref:System.Net.Sockets.Socket.Shutdown%2A> method.</span></span>  
  
 <span data-ttu-id="04f13-111">Pokud chcete přijímat data ze síťového zařízení, předejte vyrovnávací paměť jedné z metod Receive- **data třídy** DataClass ( <xref:System.Net.Sockets.Socket.Receive%2A> a <xref:System.Net.Sockets.Socket.ReceiveFrom%2A> ).</span><span class="sxs-lookup"><span data-stu-id="04f13-111">To receive data from a network device, pass a buffer to one of the **Socket** class's receive-data methods (<xref:System.Net.Sockets.Socket.Receive%2A> and <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>).</span></span> <span data-ttu-id="04f13-112">Synchronní sokety aplikaci pozastaví, dokud nejsou bajty přijímány ze sítě nebo dokud není soket uzavřen.</span><span class="sxs-lookup"><span data-stu-id="04f13-112">Synchronous sockets will suspend the application until bytes are received from the network or until the socket is closed.</span></span> <span data-ttu-id="04f13-113">Následující příklad přijímá data ze sítě a poté je zobrazuje v konzole nástroje.</span><span class="sxs-lookup"><span data-stu-id="04f13-113">The following example receives data from the network and then displays it on the console.</span></span> <span data-ttu-id="04f13-114">V příkladu se předpokládá, že data přicházející ze sítě jsou text s kódováním ASCII.</span><span class="sxs-lookup"><span data-stu-id="04f13-114">The example assumes that the data coming from the network is ASCII-encoded text.</span></span> <span data-ttu-id="04f13-115">Metoda **Receive** vrátí počet bajtů přijatých ze sítě.</span><span class="sxs-lookup"><span data-stu-id="04f13-115">The **Receive** method returns the number of bytes received from the network.</span></span>  
  
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
  
 <span data-ttu-id="04f13-116">V případě, že soket již není potřeba, je nutné jej uvolnit voláním <xref:System.Net.Sockets.Socket.Shutdown%2A> metody a následným voláním metody **Close** .</span><span class="sxs-lookup"><span data-stu-id="04f13-116">When the socket is no longer needed, you need to release it by calling the <xref:System.Net.Sockets.Socket.Shutdown%2A> method and then calling the **Close** method.</span></span> <span data-ttu-id="04f13-117">Následující příklad uvolní **soket**.</span><span class="sxs-lookup"><span data-stu-id="04f13-117">The following example releases a **Socket**.</span></span> <span data-ttu-id="04f13-118"><xref:System.Net.Sockets.SocketShutdown>Výčet definuje konstanty, které určují, zda má být soket uzavřen pro odesílání, pro příjem nebo pro obojí.</span><span class="sxs-lookup"><span data-stu-id="04f13-118">The <xref:System.Net.Sockets.SocketShutdown> enumeration defines constants that indicate whether the socket should be closed for sending, for receiving, or for both.</span></span>  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="04f13-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04f13-119">See also</span></span>

- [<span data-ttu-id="04f13-120">Použití asynchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="04f13-120">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="04f13-121">Naslouchání pomocí soketů</span><span class="sxs-lookup"><span data-stu-id="04f13-121">Listening with Sockets</span></span>](listening-with-sockets.md)
- [<span data-ttu-id="04f13-122">Příklad synchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="04f13-122">Synchronous Client Socket Example</span></span>](synchronous-client-socket-example.md)
