---
title: TCP-UDP
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
ms.openlocfilehash: d35278ab7feb42453b5a0adbc86c47b7ac3ff5ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047115"
---
# <a name="tcp-udp"></a><span data-ttu-id="c1b5a-102">TCP-UDP</span><span class="sxs-lookup"><span data-stu-id="c1b5a-102">TCP-UDP</span></span>
<span data-ttu-id="c1b5a-103">Aplikace mohou používat služby TCP (Transmission Control Protocol) a User <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Sockets.TcpListener>Datagram <xref:System.Net.Sockets.UdpClient> Protocol (UDP) s třídami , a tříd.</span><span class="sxs-lookup"><span data-stu-id="c1b5a-103">Applications can use Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) services with the <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes.</span></span> <span data-ttu-id="c1b5a-104">Tyto třídy protokolu jsou <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> postaveny na vrcholu třídy a starat se o podrobnosti přenosu dat.</span><span class="sxs-lookup"><span data-stu-id="c1b5a-104">These protocol classes are built on top of the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class and take care of the details of transferring data.</span></span>  
  
 <span data-ttu-id="c1b5a-105">Třídy protokolů používají synchronní metody třídy **Socket** k poskytování jednoduchého a jednoduchého přístupu k síťovým službám bez režie na údržbu informací o stavu nebo znalosti podrobností o nastavení soketů specifických pro protokol.</span><span class="sxs-lookup"><span data-stu-id="c1b5a-105">The protocol classes use the synchronous methods of the **Socket** class to provide simple and straightforward access to network services without the overhead of maintaining state information or knowing the details of setting up protocol-specific sockets.</span></span> <span data-ttu-id="c1b5a-106">Chcete-li použít asynchronní **Socket** metody, můžete použít asynchronní metody poskytované třídy. <xref:System.Net.Sockets.NetworkStream></span><span class="sxs-lookup"><span data-stu-id="c1b5a-106">To use asynchronous **Socket** methods, you can use the asynchronous methods supplied by the <xref:System.Net.Sockets.NetworkStream> class.</span></span> <span data-ttu-id="c1b5a-107">Chcete-li získat přístup k funkcím **třídy Socket,** které nejsou vystaveny třídám protokolu, musíte použít třídu **Socket.**</span><span class="sxs-lookup"><span data-stu-id="c1b5a-107">To access features of the **Socket** class not exposed by the protocol classes, you must use the **Socket** class.</span></span>  
  
 <span data-ttu-id="c1b5a-108">**TcpClient** a **TcpListener** představují síť pomocí třídy **NetworkStream.**</span><span class="sxs-lookup"><span data-stu-id="c1b5a-108">**TcpClient** and **TcpListener** represent the network using the **NetworkStream** class.</span></span> <span data-ttu-id="c1b5a-109"><xref:System.Net.Sockets.TcpClient.GetStream%2A> Pomocí metody vrátíte síťový proud a potom zavoláte <xref:System.Net.Sockets.NetworkStream.Read%2A> <xref:System.Net.Sockets.NetworkStream.Write%2A> datového proudu a metody.</span><span class="sxs-lookup"><span data-stu-id="c1b5a-109">You use the <xref:System.Net.Sockets.TcpClient.GetStream%2A> method to return the network stream, and then call the stream's <xref:System.Net.Sockets.NetworkStream.Read%2A> and <xref:System.Net.Sockets.NetworkStream.Write%2A> methods.</span></span> <span data-ttu-id="c1b5a-110">**NetworkStream** nevlastní základní soket třídprotokolu, takže jeho zavření nemá vliv na soket.</span><span class="sxs-lookup"><span data-stu-id="c1b5a-110">The **NetworkStream** does not own the protocol classes' underlying socket, so closing it does not affect the socket.</span></span>  
  
 <span data-ttu-id="c1b5a-111">Třída **UdpClient** používá pole bajtů pro uložení datagramu UDP.</span><span class="sxs-lookup"><span data-stu-id="c1b5a-111">The **UdpClient** class uses an array of bytes to hold the UDP datagram.</span></span> <span data-ttu-id="c1b5a-112">Tuto metodu <xref:System.Net.Sockets.UdpClient.Send%2A> použijete k odeslání dat <xref:System.Net.Sockets.UdpClient.Receive%2A> do sítě a metodu pro příjem příchozího datagramu.</span><span class="sxs-lookup"><span data-stu-id="c1b5a-112">You use the <xref:System.Net.Sockets.UdpClient.Send%2A> method to send the data to the network and the <xref:System.Net.Sockets.UdpClient.Receive%2A> method to receive an incoming datagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1b5a-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1b5a-113">See also</span></span>

- [<span data-ttu-id="c1b5a-114">Použití služeb TCP</span><span class="sxs-lookup"><span data-stu-id="c1b5a-114">Using TCP Services</span></span>](using-tcp-services.md)
- [<span data-ttu-id="c1b5a-115">Použití služeb UDP</span><span class="sxs-lookup"><span data-stu-id="c1b5a-115">Using UDP Services</span></span>](using-udp-services.md)
- [<span data-ttu-id="c1b5a-116">Použití streamů v síti</span><span class="sxs-lookup"><span data-stu-id="c1b5a-116">Using Streams on the Network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="c1b5a-117">Použití asynchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="c1b5a-117">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="c1b5a-118">Použití asynchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="c1b5a-118">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="c1b5a-119">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="c1b5a-119">Using Application Protocols</span></span>](using-application-protocols.md)
