---
title: Použití klientských soketů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- Socket class, client sockets
- protocols, sockets
- Internet, sockets
- sockets, client sockets
- client sockets
ms.assetid: 81de9f59-8177-4d98-b25d-43fc32a98383
ms.openlocfilehash: fe2ad55c3f60347369c0e92bc834d81d98f3870e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046960"
---
# <a name="using-client-sockets"></a><span data-ttu-id="50cd9-102">Použití klientských soketů</span><span class="sxs-lookup"><span data-stu-id="50cd9-102">Using Client Sockets</span></span>
<span data-ttu-id="50cd9-103">Předtím <xref:System.Net.Sockets.Socket>, než můžete zahájit konverzaci pomocí, je nutné vytvořit datový kanál mezi vaší aplikací a vzdáleným zařízením.</span><span class="sxs-lookup"><span data-stu-id="50cd9-103">Before you can initiate a conversation through a <xref:System.Net.Sockets.Socket>, you must create a data pipe between your application and the remote device.</span></span> <span data-ttu-id="50cd9-104">I když existují jiné řady síťových adres a protokoly, tento příklad ukazuje, jak vytvořit připojení TCP/IP ke vzdálené službě.</span><span class="sxs-lookup"><span data-stu-id="50cd9-104">Although other network address families and protocols exist, this example shows how to create a TCP/IP connection to a remote service.</span></span>  
  
 <span data-ttu-id="50cd9-105">Protokol TCP/IP používá k jednoznačné identifikaci služby síťovou adresu a číslo portu služby.</span><span class="sxs-lookup"><span data-stu-id="50cd9-105">TCP/IP uses a network address and a service port number to uniquely identify a service.</span></span> <span data-ttu-id="50cd9-106">Síťová adresa identifikuje konkrétní zařízení v síti. číslo portu identifikuje konkrétní službu, ke které se má toto zařízení připojit.</span><span class="sxs-lookup"><span data-stu-id="50cd9-106">The network address identifies a specific device on the network; the port number identifies the specific service on that device to connect to.</span></span> <span data-ttu-id="50cd9-107">Kombinace síťové adresy a portu služby se nazývá koncový bod, který je reprezentován v .NET Framework <xref:System.Net.EndPoint> třídy.</span><span class="sxs-lookup"><span data-stu-id="50cd9-107">The combination of network address and service port is called an endpoint, which is represented in the .NET Framework by the <xref:System.Net.EndPoint> class.</span></span> <span data-ttu-id="50cd9-108">Pro každou podporovanou rodinu adres je definován následník **koncového bodu** . pro rodinu IP adres je <xref:System.Net.IPEndPoint>třída.</span><span class="sxs-lookup"><span data-stu-id="50cd9-108">A descendant of **EndPoint** is defined for each supported address family; for the IP address family, the class is <xref:System.Net.IPEndPoint>.</span></span>  
  
 <span data-ttu-id="50cd9-109"><xref:System.Net.Dns> Třída poskytuje služby názvu domény aplikacím, které používají internetové služby TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="50cd9-109">The <xref:System.Net.Dns> class provides domain-name services to applications that use TCP/IP Internet services.</span></span> <span data-ttu-id="50cd9-110">Metoda <xref:System.Net.Dns.Resolve%2A> se dotazuje serveru DNS na mapování uživatelsky přívětivého názvu domény (například "host.contoso.com") na číselnou internetovou adresu (například 192.168.1.1).</span><span class="sxs-lookup"><span data-stu-id="50cd9-110">The <xref:System.Net.Dns.Resolve%2A> method queries a DNS server to map a user-friendly domain name (such as "host.contoso.com") to a numeric Internet address (such as 192.168.1.1).</span></span> <span data-ttu-id="50cd9-111">Funkce **Resolve** vrátí <xref:System.Net.IPHostEntry> , která obsahuje seznam adres a aliasů pro požadovaný název.</span><span class="sxs-lookup"><span data-stu-id="50cd9-111">**Resolve** returns an <xref:System.Net.IPHostEntry> that contains a list of addresses and aliases for the requested name.</span></span> <span data-ttu-id="50cd9-112">Ve většině případů můžete použít první adresu vrácenou v <xref:System.Net.IPHostEntry.AddressList%2A> poli.</span><span class="sxs-lookup"><span data-stu-id="50cd9-112">In most cases, you can use the first address returned in the <xref:System.Net.IPHostEntry.AddressList%2A> array.</span></span> <span data-ttu-id="50cd9-113">Následující kód získá <xref:System.Net.IPAddress> adresu obsahující IP adresu pro Server Host.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="50cd9-113">The following code gets an <xref:System.Net.IPAddress> containing the IP address for the server host.contoso.com.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 <span data-ttu-id="50cd9-114">Internet Assigned Numbers Authority (IANA) definuje čísla portů pro běžné služby (Další informace najdete v části [Service Name and Transport Protocol Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span><span class="sxs-lookup"><span data-stu-id="50cd9-114">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (for more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="50cd9-115">Jiné služby můžou mít registrovaná čísla portů v rozsahu 1 024 až 65 535.</span><span class="sxs-lookup"><span data-stu-id="50cd9-115">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span> <span data-ttu-id="50cd9-116">Následující kód kombinuje IP adresu pro host.contoso.com s číslem portu pro vytvoření vzdáleného koncového bodu pro připojení.</span><span class="sxs-lookup"><span data-stu-id="50cd9-116">The following code combines the IP address for host.contoso.com with a port number to create a remote endpoint for a connection.</span></span>  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 <span data-ttu-id="50cd9-117">Po určení adresy vzdáleného zařízení a výběru portu, který se má použít pro připojení, se aplikace může pokusit připojit ke vzdálenému zařízení.</span><span class="sxs-lookup"><span data-stu-id="50cd9-117">After determining the address of the remote device and choosing a port to use for the connection, the application can attempt to establish a connection with the remote device.</span></span> <span data-ttu-id="50cd9-118">Následující příklad používá existující **IPEndPoint** pro připojení ke vzdálenému zařízení a zachycuje všechny výjimky, které jsou vyvolány.</span><span class="sxs-lookup"><span data-stu-id="50cd9-118">The following example uses an existing **IPEndPoint** to connect to a remote device and catches any exceptions that are thrown.</span></span>  
  
```vb  
Try  
    s.Connect(ipe)  
Catch ae As ArgumentNullException  
    Console.WriteLine("ArgumentNullException : {0}", _  
        ae.ToString())  
Catch se As SocketException  
    Console.WriteLine("SocketException : {0}", se.ToString())  
Catch e As Exception  
    Console.WriteLine("Unexpected exception : {0}", e.ToString())  
End Try  
```  
  
```csharp  
try {  
    s.Connect(ipe);  
} catch(ArgumentNullException ae) {  
    Console.WriteLine("ArgumentNullException : {0}", ae.ToString());  
} catch(SocketException se) {  
    Console.WriteLine("SocketException : {0}", se.ToString());  
} catch(Exception e) {  
    Console.WriteLine("Unexpected exception : {0}", e.ToString());  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="50cd9-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50cd9-119">See also</span></span>

- [<span data-ttu-id="50cd9-120">Použití synchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="50cd9-120">Using a Synchronous Client Socket</span></span>](using-a-synchronous-client-socket.md)
- [<span data-ttu-id="50cd9-121">Použití asynchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="50cd9-121">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="50cd9-122">Postupy: Vytvoření soketu</span><span class="sxs-lookup"><span data-stu-id="50cd9-122">How to: Create a Socket</span></span>](how-to-create-a-socket.md)
- [<span data-ttu-id="50cd9-123">Sokety</span><span class="sxs-lookup"><span data-stu-id="50cd9-123">Sockets</span></span>](sockets.md)
