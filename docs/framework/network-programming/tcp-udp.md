---
title: TCP UDP
ms.date: 03/30/2017
helpviewer_keywords:
- protocols, TCP/UDP
- network resources, TCP/UDP
- sending data, TCP/UDP
- TCP/UDP
- TcpClient class, about TcpClient class
- application protocols, TCP/UDP
- receiving data, TCP/UDP
- TcpListener class, about TcpListener class
- Socket class, about Socket class
- UDP
- data requests, TCP/UDP
- requesting data from Internet, TCP/UDP
- Internet, TCP/UDP
ms.assetid: df29b4b0-49e8-4923-82b9-13150dfc40f5
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 30630f397d491a6a5f251ddac14a4db90e53b999
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394602"
---
# <a name="tcp-udp"></a><span data-ttu-id="06154-102">TCP UDP</span><span class="sxs-lookup"><span data-stu-id="06154-102">TCP-UDP</span></span>
<span data-ttu-id="06154-103">Aplikace můžete použít protokol TCP (Transmission Control) a protokolu UDP (User Datagram) služby pomocí <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, a <xref:System.Net.Sockets.UdpClient> třídy.</span><span class="sxs-lookup"><span data-stu-id="06154-103">Applications can use Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) services with the <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes.</span></span> <span data-ttu-id="06154-104">Tyto třídy protokolu jsou postavený na <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> třídy a postará o podrobnosti o přenosu dat.</span><span class="sxs-lookup"><span data-stu-id="06154-104">These protocol classes are built on top of the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class and take care of the details of transferring data.</span></span>  
  
 <span data-ttu-id="06154-105">Třídy protokol použít synchronní metody sady **soketu** třídy poskytují jednoduchá a přímočará přístup k síťovým službám bez nutnosti zachování informací o stavu nebo znát podrobnosti o nastavení sokety specifické pro protokol.</span><span class="sxs-lookup"><span data-stu-id="06154-105">The protocol classes use the synchronous methods of the **Socket** class to provide simple and straightforward access to network services without the overhead of maintaining state information or knowing the details of setting up protocol-specific sockets.</span></span> <span data-ttu-id="06154-106">Použít asynchronní **soketu** metod, můžete použít asynchronní metody poskytl <xref:System.Net.Sockets.NetworkStream> třídy.</span><span class="sxs-lookup"><span data-stu-id="06154-106">To use asynchronous **Socket** methods, you can use the asynchronous methods supplied by the <xref:System.Net.Sockets.NetworkStream> class.</span></span> <span data-ttu-id="06154-107">Pro přístup k funkcím z **soketu** třídy nejsou viditelné protocol třídami, je nutné použít **soketu** – třída.</span><span class="sxs-lookup"><span data-stu-id="06154-107">To access features of the **Socket** class not exposed by the protocol classes, you must use the **Socket** class.</span></span>  
  
 <span data-ttu-id="06154-108">**TcpClient** a **TcpListener** představují síti pomocí **NetworkStream** třídy.</span><span class="sxs-lookup"><span data-stu-id="06154-108">**TcpClient** and **TcpListener** represent the network using the **NetworkStream** class.</span></span> <span data-ttu-id="06154-109">Můžete použít <xref:System.Net.Sockets.TcpClient.GetStream%2A> má metoda vrátit datový proud sítě a pak zavolají datový proud <xref:System.Net.Sockets.NetworkStream.Read%2A> a <xref:System.Net.Sockets.NetworkStream.Write%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="06154-109">You use the <xref:System.Net.Sockets.TcpClient.GetStream%2A> method to return the network stream, and then call the stream's <xref:System.Net.Sockets.NetworkStream.Read%2A> and <xref:System.Net.Sockets.NetworkStream.Write%2A> methods.</span></span> <span data-ttu-id="06154-110">**NetworkStream** nevlastní protokol třídy základní soketu, takže zavřením nemá vliv na soket.</span><span class="sxs-lookup"><span data-stu-id="06154-110">The **NetworkStream** does not own the protocol classes' underlying socket, so closing it does not affect the socket.</span></span>  
  
 <span data-ttu-id="06154-111">**UdpClient** třída používá pro uložení datagramů UDP pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="06154-111">The **UdpClient** class uses an array of bytes to hold the UDP datagram.</span></span> <span data-ttu-id="06154-112">Můžete použít <xref:System.Net.Sockets.UdpClient.Send%2A> metodu pro odeslání dat do sítě a <xref:System.Net.Sockets.UdpClient.Receive%2A> metodu datagramu příchozí.</span><span class="sxs-lookup"><span data-stu-id="06154-112">You use the <xref:System.Net.Sockets.UdpClient.Send%2A> method to send the data to the network and the <xref:System.Net.Sockets.UdpClient.Receive%2A> method to receive an incoming datagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06154-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="06154-113">See Also</span></span>  
 [<span data-ttu-id="06154-114">Použití služeb TCP</span><span class="sxs-lookup"><span data-stu-id="06154-114">Using TCP Services</span></span>](../../../docs/framework/network-programming/using-tcp-services.md)  
 [<span data-ttu-id="06154-115">Použití služeb UDP</span><span class="sxs-lookup"><span data-stu-id="06154-115">Using UDP Services</span></span>](../../../docs/framework/network-programming/using-udp-services.md)  
 [<span data-ttu-id="06154-116">Použití streamů v síti</span><span class="sxs-lookup"><span data-stu-id="06154-116">Using Streams on the Network</span></span>](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [<span data-ttu-id="06154-117">Použití asynchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="06154-117">Using an Asynchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [<span data-ttu-id="06154-118">Použití asynchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="06154-118">Using an Asynchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [<span data-ttu-id="06154-119">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="06154-119">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
