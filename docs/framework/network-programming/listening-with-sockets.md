---
title: Poslech s sokety
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
ms.openlocfilehash: d8db8cc6157ef0b03c90d00804696c7e660f08a3
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736782"
---
# <a name="listening-with-sockets"></a><span data-ttu-id="84f97-102">Poslech s sokety</span><span class="sxs-lookup"><span data-stu-id="84f97-102">Listening with Sockets</span></span>
<span data-ttu-id="84f97-103">Naslouchací proces nebo serverové sokety otevřou port v síti a pak čekají na připojení klienta k tomuto portu.</span><span class="sxs-lookup"><span data-stu-id="84f97-103">Listener or server sockets open a port on the network and then wait for a client to connect to that port.</span></span> <span data-ttu-id="84f97-104">I když existují další řady síťových adres a protokoly, tento příklad ukazuje, jak vytvořit vzdálenou službu pro síť TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="84f97-104">Although other network address families and protocols exist, this example shows how to create remote service for a TCP/IP network.</span></span>  
  
 <span data-ttu-id="84f97-105">Jedinečná adresa služby TCP/IP je definovaná kombinací IP adresy hostitele s číslem portu služby, aby se vytvořil koncový bod pro službu.</span><span class="sxs-lookup"><span data-stu-id="84f97-105">The unique address of a TCP/IP service is defined by combining the IP address of the host with the port number of the service to create an endpoint for the service.</span></span> <span data-ttu-id="84f97-106">Třída <xref:System.Net.Dns> poskytuje metody, které vracejí informace o síťových adresách podporovaných místním síťovým zařízením.</span><span class="sxs-lookup"><span data-stu-id="84f97-106">The <xref:System.Net.Dns> class provides methods that return information about the network addresses supported by the local network device.</span></span> <span data-ttu-id="84f97-107">Pokud má místní síťové zařízení více než jednu síťovou adresu nebo pokud místní systém podporuje více než jedno síťové zařízení, vrátí třída **DNS** informace o všech síťových adresách a aplikace musí zvolit správnou adresu služby.</span><span class="sxs-lookup"><span data-stu-id="84f97-107">When the local network device has more than one network address, or if the local system supports more than one network device, the **Dns** class returns information about all network addresses, and the application must choose the proper address for the service.</span></span> <span data-ttu-id="84f97-108">Autorita pro Internet Assigned Numbers Authority (IANA) definuje čísla portů pro běžné služby. Další informace najdete v části [Service Name and Transport Protocol Number Registry](https://www.iana.org/assignments/port-numbers).</span><span class="sxs-lookup"><span data-stu-id="84f97-108">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services; for more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="84f97-109">Jiné služby můžou mít registrovaná čísla portů v rozsahu 1 024 až 65 535.</span><span class="sxs-lookup"><span data-stu-id="84f97-109">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="84f97-110">Následující příklad vytvoří <xref:System.Net.IPEndPoint> pro server tím, že kombinuje první IP adresu vrácenou **DNS** pro hostitelský počítač s číslem portu vybraným z rozsahu registrovaných čísel portů.</span><span class="sxs-lookup"><span data-stu-id="84f97-110">The following example creates an <xref:System.Net.IPEndPoint> for a server by combining the first IP address returned by **Dns** for the host computer with a port number chosen from the registered port numbers range.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.GetHostEntry(Dns.GetHostName())  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.GetHostEntry(Dns.GetHostName());  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
```  
  
 <span data-ttu-id="84f97-111">Po určení místního koncového bodu musí být <xref:System.Net.Sockets.Socket> přidružen k tomuto koncovému bodu pomocí metody <xref:System.Net.Sockets.Socket.Bind%2A> a nastavit k naslouchání na koncovém bodu pomocí metody <xref:System.Net.Sockets.Socket.Listen%2A>.</span><span class="sxs-lookup"><span data-stu-id="84f97-111">After the local endpoint is determined, the <xref:System.Net.Sockets.Socket> must be associated with that endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> method and set to listen on the endpoint using the <xref:System.Net.Sockets.Socket.Listen%2A> method.</span></span> <span data-ttu-id="84f97-112">**Vazba** vyvolá výjimku, pokud se již používá specifická adresa a kombinace portů.</span><span class="sxs-lookup"><span data-stu-id="84f97-112">**Bind** throws an exception if the specific address and port combination is already in use.</span></span> <span data-ttu-id="84f97-113">Následující příklad ukazuje přidružení **soketu** k **IPEndPoint**.</span><span class="sxs-lookup"><span data-stu-id="84f97-113">The following example demonstrates associating a **Socket** with an **IPEndPoint**.</span></span>  
  
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
  
 <span data-ttu-id="84f97-114">Metoda **Listen** přijímá jeden parametr, který určuje, kolik nedokončených připojení k **soketu** je povoleno před tím, než dojde k chybě zaneprázdnění serveru v připojujícím se klientovi.</span><span class="sxs-lookup"><span data-stu-id="84f97-114">The **Listen** method takes a single parameter that specifies how many pending connections to the **Socket** are allowed before a server busy error is returned to the connecting client.</span></span> <span data-ttu-id="84f97-115">V takovém případě se až 100 klientů umístí do fronty připojení před tím, než se vrátí odpověď zaneprázdněného serveru na číslo klienta 101.</span><span class="sxs-lookup"><span data-stu-id="84f97-115">In this case, up to 100 clients are placed in the connection queue before a server busy response is returned to client number 101.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84f97-116">Další informace najdete v tématech</span><span class="sxs-lookup"><span data-stu-id="84f97-116">See also</span></span>

- [<span data-ttu-id="84f97-117">Použití synchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="84f97-117">Using a Synchronous Server Socket</span></span>](using-a-synchronous-server-socket.md)
- [<span data-ttu-id="84f97-118">Použití asynchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="84f97-118">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="84f97-119">Použití klientských soketů</span><span class="sxs-lookup"><span data-stu-id="84f97-119">Using Client Sockets</span></span>](using-client-sockets.md)
- [<span data-ttu-id="84f97-120">Postupy: Vytvoření soketu</span><span class="sxs-lookup"><span data-stu-id="84f97-120">How to: Create a Socket</span></span>](how-to-create-a-socket.md)
- [<span data-ttu-id="84f97-121">Zásuvky</span><span class="sxs-lookup"><span data-stu-id="84f97-121">Sockets</span></span>](sockets.md)
