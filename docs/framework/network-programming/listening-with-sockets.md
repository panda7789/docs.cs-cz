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
ms.openlocfilehash: cf8316ede6888b99a8b0c87cfa3426b33be18b7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180744"
---
# <a name="listening-with-sockets"></a><span data-ttu-id="99841-102">Naslouchání pomocí soketů</span><span class="sxs-lookup"><span data-stu-id="99841-102">Listening with Sockets</span></span>
<span data-ttu-id="99841-103">Naslouchací proces nebo sokety serveru otevřou port v síti a počkejte, až se klient k tomuto portu připojí.</span><span class="sxs-lookup"><span data-stu-id="99841-103">Listener or server sockets open a port on the network and then wait for a client to connect to that port.</span></span> <span data-ttu-id="99841-104">Přestože existují jiné rodiny síťových adres a protokoly, tento příklad ukazuje, jak vytvořit vzdálenou službu pro síť TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="99841-104">Although other network address families and protocols exist, this example shows how to create remote service for a TCP/IP network.</span></span>  
  
 <span data-ttu-id="99841-105">Jedinečná adresa služby TCP/IP je definována kombinací IP adresy hostitele s číslem portu služby a vytvořením koncového bodu pro službu.</span><span class="sxs-lookup"><span data-stu-id="99841-105">The unique address of a TCP/IP service is defined by combining the IP address of the host with the port number of the service to create an endpoint for the service.</span></span> <span data-ttu-id="99841-106">Třída <xref:System.Net.Dns> poskytuje metody, které vracejí informace o síťových adresách podporovaných místním síťovým zařízením.</span><span class="sxs-lookup"><span data-stu-id="99841-106">The <xref:System.Net.Dns> class provides methods that return information about the network addresses supported by the local network device.</span></span> <span data-ttu-id="99841-107">Pokud má místní síťové zařízení více než jednu síťovou adresu nebo pokud místní systém podporuje více než jedno síťové zařízení, vrátí třída **DNS** informace o všech síťových adresách a aplikace musí zvolit správnou adresu služby.</span><span class="sxs-lookup"><span data-stu-id="99841-107">When the local network device has more than one network address, or if the local system supports more than one network device, the **Dns** class returns information about all network addresses, and the application must choose the proper address for the service.</span></span> <span data-ttu-id="99841-108">Internetová autorita pro přiřazená čísla (Iana) definuje čísla portů pro běžné služby; Další informace naleznete v [tématu Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/port-numbers).</span><span class="sxs-lookup"><span data-stu-id="99841-108">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services; for more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="99841-109">Ostatní služby mohou mít registrovaná čísla portů v rozsahu 1 024 až 65 535.</span><span class="sxs-lookup"><span data-stu-id="99841-109">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="99841-110">Následující příklad vytvoří <xref:System.Net.IPEndPoint> pro server kombinací první IP adresy vrácené **službou DNS** pro hostitelský počítač s číslem portu vybraným z rozsahu registrovaných čísel portů.</span><span class="sxs-lookup"><span data-stu-id="99841-110">The following example creates an <xref:System.Net.IPEndPoint> for a server by combining the first IP address returned by **Dns** for the host computer with a port number chosen from the registered port numbers range.</span></span>  
  
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
  
 <span data-ttu-id="99841-111">Po určení místního koncového <xref:System.Net.Sockets.Socket> bodu musí být přidružený <xref:System.Net.Sockets.Socket.Bind%2A> k tomuto koncovému bodu pomocí <xref:System.Net.Sockets.Socket.Listen%2A> metody a nastavit naslouchání na koncovém bodu pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="99841-111">After the local endpoint is determined, the <xref:System.Net.Sockets.Socket> must be associated with that endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> method and set to listen on the endpoint using the <xref:System.Net.Sockets.Socket.Listen%2A> method.</span></span> <span data-ttu-id="99841-112">**Vazba** vyvolá výjimku, pokud je konkrétní kombinace adresy a portu již používána.</span><span class="sxs-lookup"><span data-stu-id="99841-112">**Bind** throws an exception if the specific address and port combination is already in use.</span></span> <span data-ttu-id="99841-113">Následující příklad ukazuje spojení **Socket** s **IPEndPoint**.</span><span class="sxs-lookup"><span data-stu-id="99841-113">The following example demonstrates associating a **Socket** with an **IPEndPoint**.</span></span>  
  
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
  
 <span data-ttu-id="99841-114">Metoda **Listen** přebírá jeden parametr, který určuje, kolik čekajících připojení k **Socket** uvolňuje před vrácením chyby zaneprázdněnserveru připojujícímu se klientovi.</span><span class="sxs-lookup"><span data-stu-id="99841-114">The **Listen** method takes a single parameter that specifies how many pending connections to the **Socket** are allowed before a server busy error is returned to the connecting client.</span></span> <span data-ttu-id="99841-115">V tomto případě je do fronty připojení umístěno až 100 klientů před vrácením odpovědi serveru zaneprázdněn na číslo klienta 101.</span><span class="sxs-lookup"><span data-stu-id="99841-115">In this case, up to 100 clients are placed in the connection queue before a server busy response is returned to client number 101.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99841-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="99841-116">See also</span></span>

- [<span data-ttu-id="99841-117">Použití synchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="99841-117">Using a Synchronous Server Socket</span></span>](using-a-synchronous-server-socket.md)
- [<span data-ttu-id="99841-118">Použití asynchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="99841-118">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="99841-119">Použití klientských soketů</span><span class="sxs-lookup"><span data-stu-id="99841-119">Using Client Sockets</span></span>](using-client-sockets.md)
- [<span data-ttu-id="99841-120">Postupy: Vytvoření soketu</span><span class="sxs-lookup"><span data-stu-id="99841-120">How to: Create a Socket</span></span>](how-to-create-a-socket.md)
- [<span data-ttu-id="99841-121">Sokety</span><span class="sxs-lookup"><span data-stu-id="99841-121">Sockets</span></span>](sockets.md)
