---
title: Naslouchání pomocí soketů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- sockets, listening with sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- protocols, sockets
- listening with sockets
- Internet, sockets
ms.assetid: 40e426cc-13db-4371-95eb-f7388bd23ebf
ms.openlocfilehash: c3d5a7d6040038eb6d768815b1ae9e8ad45c5810
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642214"
---
# <a name="listening-with-sockets"></a><span data-ttu-id="c7b6a-102">Naslouchání pomocí soketů</span><span class="sxs-lookup"><span data-stu-id="c7b6a-102">Listening with Sockets</span></span>
<span data-ttu-id="c7b6a-103">Naslouchací proces nebo server sockets otevření portu v síti a potom počkejte klienta pro připojení k tomuto portu.</span><span class="sxs-lookup"><span data-stu-id="c7b6a-103">Listener or server sockets open a port on the network and then wait for a client to connect to that port.</span></span> <span data-ttu-id="c7b6a-104">I když existují jiné rodiny adres sítě a protokoly, tento příklad ukazuje, jak vytvořit vzdálené služby pro sítě TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="c7b6a-104">Although other network address families and protocols exist, this example shows how to create remote service for a TCP/IP network.</span></span>  
  
 <span data-ttu-id="c7b6a-105">Díky kombinaci IP adresu hostitele s použitím čísla portu služby vytvořit koncový bod služby je definován jedinečnou adresu služby TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="c7b6a-105">The unique address of a TCP/IP service is defined by combining the IP address of the host with the port number of the service to create an endpoint for the service.</span></span> <span data-ttu-id="c7b6a-106"><xref:System.Net.Dns> Třída poskytuje metody, které vracejí informace o síťové adresy místní síťové zařízení podporuje.</span><span class="sxs-lookup"><span data-stu-id="c7b6a-106">The <xref:System.Net.Dns> class provides methods that return information about the network addresses supported by the local network device.</span></span> <span data-ttu-id="c7b6a-107">Když zařízení místní sítě má více než jednu síťovou adresu, nebo místní systém podporuje více než jedno síťové zařízení, **Dns** třída vrací informace o všech síťových adres, a aplikace musíte vybrat správné Adresa pro službu.</span><span class="sxs-lookup"><span data-stu-id="c7b6a-107">When the local network device has more than one network address, or if the local system supports more than one network device, the **Dns** class returns information about all network addresses, and the application must choose the proper address for the service.</span></span> <span data-ttu-id="c7b6a-108">Internet Assigned Numbers Authority (Iana) definuje čísla portů pro běžné služby; Další informace najdete v tématu [název služby a registru číslo portu protokolu přenosu](https://www.iana.org/assignments/port-numbers).</span><span class="sxs-lookup"><span data-stu-id="c7b6a-108">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services; for more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="c7b6a-109">Další služby můžou jste se zaregistrovali čísla portu v rozsahu 1 024 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="c7b6a-109">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="c7b6a-110">Následující příklad vytvoří <xref:System.Net.IPEndPoint> pro server kombinací první IP adresu vrácenou **Dns** pro hostitelský počítač s číslem portu zvolit rozsah čísel registrovaných portů.</span><span class="sxs-lookup"><span data-stu-id="c7b6a-110">The following example creates an <xref:System.Net.IPEndPoint> for a server by combining the first IP address returned by **Dns** for the host computer with a port number chosen from the registered port numbers range.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
```  
  
 <span data-ttu-id="c7b6a-111">Po místním koncovým bodem je určit, <xref:System.Net.Sockets.Socket> musí být přidružen pomocí tohoto koncového bodu <xref:System.Net.Sockets.Socket.Bind%2A> metoda a nastavte tak, aby naslouchala na koncový bod pomocí <xref:System.Net.Sockets.Socket.Listen%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="c7b6a-111">After the local endpoint is determined, the <xref:System.Net.Sockets.Socket> must be associated with that endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> method and set to listen on the endpoint using the <xref:System.Net.Sockets.Socket.Listen%2A> method.</span></span> <span data-ttu-id="c7b6a-112">**Vytvoření vazby** vyvolá výjimku, pokud se konkrétní kombinaci adresu a port je již používán.</span><span class="sxs-lookup"><span data-stu-id="c7b6a-112">**Bind** throws an exception if the specific address and port combination is already in use.</span></span> <span data-ttu-id="c7b6a-113">Následující příklad ukazuje přidružení **soketu** s **IPEndPoint**.</span><span class="sxs-lookup"><span data-stu-id="c7b6a-113">The following example demonstrates associating a **Socket** with an **IPEndPoint**.</span></span>  
  
```vb  
Dim listener As New Socket(ipAddress.AddressFamily, _  
    SocketType.Stream, ProtocolType.Tcp) 
listener.Bind(localEndPoint)  
listener.Listen(100)  
```  
  
```csharp  
Socket listener = new Socket(ipAddress.AddressFamily,
    SocketType.Stream, ProtocolType.Tcp);
listener.Bind(localEndPoint);  
listener.Listen(100);  
```  
  
 <span data-ttu-id="c7b6a-114">**Naslouchání** metoda přijímá jeden parametr, který určuje, kolik čeká na připojení k **soketu** jsou povoleny před chybu zaneprázdněný server se vrátí do připojujícího se klienta.</span><span class="sxs-lookup"><span data-stu-id="c7b6a-114">The **Listen** method takes a single parameter that specifies how many pending connections to the **Socket** are allowed before a server busy error is returned to the connecting client.</span></span> <span data-ttu-id="c7b6a-115">V takovém případě až 100 klientů jsou umístěné ve frontě připojení předtím, než je server zaneprázdněný odpověď se vrátí do klienta číslem 101.</span><span class="sxs-lookup"><span data-stu-id="c7b6a-115">In this case, up to 100 clients are placed in the connection queue before a server busy response is returned to client number 101.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7b6a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7b6a-116">See also</span></span>

- [<span data-ttu-id="c7b6a-117">Použití synchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="c7b6a-117">Using a Synchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)
- [<span data-ttu-id="c7b6a-118">Použití asynchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="c7b6a-118">Using an Asynchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="c7b6a-119">Použití klientských soketů</span><span class="sxs-lookup"><span data-stu-id="c7b6a-119">Using Client Sockets</span></span>](../../../docs/framework/network-programming/using-client-sockets.md)
- [<span data-ttu-id="c7b6a-120">Postupy: Vytvoření soketu</span><span class="sxs-lookup"><span data-stu-id="c7b6a-120">How to: Create a Socket</span></span>](../../../docs/framework/network-programming/how-to-create-a-socket.md)
- [<span data-ttu-id="c7b6a-121">Sokety</span><span class="sxs-lookup"><span data-stu-id="c7b6a-121">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
