---
title: Použití klienta soketů
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 458e67861bfd40b69f7a6f756ddee8be433e9e2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395944"
---
# <a name="using-client-sockets"></a><span data-ttu-id="c1d8e-102">Použití klienta soketů</span><span class="sxs-lookup"><span data-stu-id="c1d8e-102">Using Client Sockets</span></span>
<span data-ttu-id="c1d8e-103">Před spuštěním konverzace prostřednictvím <xref:System.Net.Sockets.Socket>, je nutné vytvořit datového kanálu mezi vaší aplikací a vzdálená zařízení.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-103">Before you can initiate a conversation through a <xref:System.Net.Sockets.Socket>, you must create a data pipe between your application and the remote device.</span></span> <span data-ttu-id="c1d8e-104">I když existují další rodiny adres sítě a protokoly, tento příklad ukazuje postup vytvoření připojení TCP/IP k vzdálené služby.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-104">Although other network address families and protocols exist, this example shows how to create a TCP/IP connection to a remote service.</span></span>  
  
 <span data-ttu-id="c1d8e-105">TCP/IP používá síťová adresa a číslo portu služby k jednoznačné identifikaci služby.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-105">TCP/IP uses a network address and a service port number to uniquely identify a service.</span></span> <span data-ttu-id="c1d8e-106">Síťová adresa identifikuje určité zařízení v síti; číslo portu identifikuje specifické služby v tomto zařízení pro připojení k.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-106">The network address identifies a specific device on the network; the port number identifies the specific service on that device to connect to.</span></span> <span data-ttu-id="c1d8e-107">Kombinace portu síťového adresu a služby se nazývá koncový bod, který je reprezentován v rozhraní .NET Framework pomocí <xref:System.Net.EndPoint> třídy.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-107">The combination of network address and service port is called an endpoint, which is represented in the .NET Framework by the <xref:System.Net.EndPoint> class.</span></span> <span data-ttu-id="c1d8e-108">Následníka **koncový bod** je definována pro všechny podporované rodina adres; pro rodina IP adres, je třída <xref:System.Net.IPEndPoint>.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-108">A descendant of **EndPoint** is defined for each supported address family; for the IP address family, the class is <xref:System.Net.IPEndPoint>.</span></span>  
  
 <span data-ttu-id="c1d8e-109"><xref:System.Net.Dns> Třída poskytuje název domény služby pro aplikace, které používají protokol TCP/IP internetové služby.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-109">The <xref:System.Net.Dns> class provides domain-name services to applications that use TCP/IP Internet services.</span></span> <span data-ttu-id="c1d8e-110"><xref:System.Net.Dns.Resolve%2A> Metoda dotazuje serveru DNS pro mapování názvu uživatelsky přívětivý domény (například "host.contoso.com") na číselné internetové adresy (jako je například 192.168.1.1).</span><span class="sxs-lookup"><span data-stu-id="c1d8e-110">The <xref:System.Net.Dns.Resolve%2A> method queries a DNS server to map a user-friendly domain name (such as "host.contoso.com") to a numeric Internet address (such as 192.168.1.1).</span></span> <span data-ttu-id="c1d8e-111">**Vyřešte** vrátí <xref:System.Net.IPHostEntry> obsahující seznam adres a aliasy pro požadovaný název.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-111">**Resolve** returns an <xref:System.Net.IPHostEntry> that contains a list of addresses and aliases for the requested name.</span></span> <span data-ttu-id="c1d8e-112">Ve většině případů můžete použít první adresu vrácenou v <xref:System.Net.IPHostEntry.AddressList%2A> pole.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-112">In most cases, you can use the first address returned in the <xref:System.Net.IPHostEntry.AddressList%2A> array.</span></span> <span data-ttu-id="c1d8e-113">Následující kód získá <xref:System.Net.IPAddress> obsahující IP adresu pro host.contoso.com serveru.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-113">The following code gets an <xref:System.Net.IPAddress> containing the IP address for the server host.contoso.com.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 <span data-ttu-id="c1d8e-114">Internet Assigned Numbers Authority (Iana) definuje čísla portů pro běžné služby (pro další informace najdete v tématu www.iana.org/assignments/port-numbers).</span><span class="sxs-lookup"><span data-stu-id="c1d8e-114">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (for more information, see www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="c1d8e-115">Další služby můžete zaregistrovat čísla portů v rozsahu 1 024 jednotek do 65 535.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-115">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span> <span data-ttu-id="c1d8e-116">Následující kód spojuje IP adresu pro host.contoso.com se číslo portu k vytvoření vzdálený koncový bod pro připojení.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-116">The following code combines the IP address for host.contoso.com with a port number to create a remote endpoint for a connection.</span></span>  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 <span data-ttu-id="c1d8e-117">Po určení adresa vzdáleného zařízení a zvolením port pro připojení, můžete aplikaci pokusí navázat připojení se vzdáleným zařízením.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-117">After determining the address of the remote device and choosing a port to use for the connection, the application can attempt to establish a connection with the remote device.</span></span> <span data-ttu-id="c1d8e-118">Následující příklad používá existující **IPEndPoint** pro připojení k vzdálené zařízení a zachytí všechny výjimky, které jsou vydány.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-118">The following example uses an existing **IPEndPoint** to connect to a remote device and catches any exceptions that are thrown.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c1d8e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1d8e-119">See Also</span></span>  
 [<span data-ttu-id="c1d8e-120">Použití synchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="c1d8e-120">Using a Synchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)  
 [<span data-ttu-id="c1d8e-121">Použití asynchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="c1d8e-121">Using an Asynchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [<span data-ttu-id="c1d8e-122">Postupy: Vytvoření soketu</span><span class="sxs-lookup"><span data-stu-id="c1d8e-122">How to: Create a Socket</span></span>](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
 [<span data-ttu-id="c1d8e-123">Sokety</span><span class="sxs-lookup"><span data-stu-id="c1d8e-123">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
