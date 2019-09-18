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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047115"
---
# <a name="tcp-udp"></a><span data-ttu-id="32d21-102">TCP-UDP</span><span class="sxs-lookup"><span data-stu-id="32d21-102">TCP-UDP</span></span>
<span data-ttu-id="32d21-103">Aplikace mohou používat služby protokolu TCP (Transmission Control Protocol) a UDP (User Datagram Protocol) s <xref:System.Net.Sockets.TcpClient>třídami, <xref:System.Net.Sockets.UdpClient> <xref:System.Net.Sockets.TcpListener>a.</span><span class="sxs-lookup"><span data-stu-id="32d21-103">Applications can use Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) services with the <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes.</span></span> <span data-ttu-id="32d21-104">Tyto třídy protokolu jsou postaveny nad <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> třídou a postarou se o podrobnosti přenosu dat.</span><span class="sxs-lookup"><span data-stu-id="32d21-104">These protocol classes are built on top of the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class and take care of the details of transferring data.</span></span>  
  
 <span data-ttu-id="32d21-105">Třídy protokolu používají synchronní metody třídy **Socket** k poskytování jednoduchého a jednoduššího přístupu k síťovým službám bez režie údržby stavových informací nebo zjištění podrobností o nastavení soketů specifických pro protokol.</span><span class="sxs-lookup"><span data-stu-id="32d21-105">The protocol classes use the synchronous methods of the **Socket** class to provide simple and straightforward access to network services without the overhead of maintaining state information or knowing the details of setting up protocol-specific sockets.</span></span> <span data-ttu-id="32d21-106">Chcete-li použít metody asynchronního **soketu** , můžete použít asynchronní metody poskytované <xref:System.Net.Sockets.NetworkStream> třídou.</span><span class="sxs-lookup"><span data-stu-id="32d21-106">To use asynchronous **Socket** methods, you can use the asynchronous methods supplied by the <xref:System.Net.Sockets.NetworkStream> class.</span></span> <span data-ttu-id="32d21-107">Chcete-li získat přístup k funkcím třídy **Socket** , která není vystavena třídami protokolu, je nutné použít třídu **Socket** .</span><span class="sxs-lookup"><span data-stu-id="32d21-107">To access features of the **Socket** class not exposed by the protocol classes, you must use the **Socket** class.</span></span>  
  
 <span data-ttu-id="32d21-108">**TcpClient** a **Třída TcpListener nesmí** reprezentují síť pomocí třídy **NetworkStream** .</span><span class="sxs-lookup"><span data-stu-id="32d21-108">**TcpClient** and **TcpListener** represent the network using the **NetworkStream** class.</span></span> <span data-ttu-id="32d21-109">Použijte <xref:System.Net.Sockets.TcpClient.GetStream%2A> metodu k vrácení síťového datového proudu a pak zavolejte <xref:System.Net.Sockets.NetworkStream.Read%2A> metody a <xref:System.Net.Sockets.NetworkStream.Write%2A> .</span><span class="sxs-lookup"><span data-stu-id="32d21-109">You use the <xref:System.Net.Sockets.TcpClient.GetStream%2A> method to return the network stream, and then call the stream's <xref:System.Net.Sockets.NetworkStream.Read%2A> and <xref:System.Net.Sockets.NetworkStream.Write%2A> methods.</span></span> <span data-ttu-id="32d21-110">**NetworkStream** nevlastní základní soket tříd protokolů, takže jeho zavření nemá vliv na soket.</span><span class="sxs-lookup"><span data-stu-id="32d21-110">The **NetworkStream** does not own the protocol classes' underlying socket, so closing it does not affect the socket.</span></span>  
  
 <span data-ttu-id="32d21-111">Třída **UdpClient** používá pole bajtů k uložení datagramu UDP.</span><span class="sxs-lookup"><span data-stu-id="32d21-111">The **UdpClient** class uses an array of bytes to hold the UDP datagram.</span></span> <span data-ttu-id="32d21-112">Použijte <xref:System.Net.Sockets.UdpClient.Send%2A> metodu k odeslání dat do sítě <xref:System.Net.Sockets.UdpClient.Receive%2A> a metody pro příjem příchozího datagramu.</span><span class="sxs-lookup"><span data-stu-id="32d21-112">You use the <xref:System.Net.Sockets.UdpClient.Send%2A> method to send the data to the network and the <xref:System.Net.Sockets.UdpClient.Receive%2A> method to receive an incoming datagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32d21-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32d21-113">See also</span></span>

- [<span data-ttu-id="32d21-114">Použití služeb TCP</span><span class="sxs-lookup"><span data-stu-id="32d21-114">Using TCP Services</span></span>](using-tcp-services.md)
- [<span data-ttu-id="32d21-115">Použití služeb UDP</span><span class="sxs-lookup"><span data-stu-id="32d21-115">Using UDP Services</span></span>](using-udp-services.md)
- [<span data-ttu-id="32d21-116">Použití streamů v síti</span><span class="sxs-lookup"><span data-stu-id="32d21-116">Using Streams on the Network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="32d21-117">Použití asynchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="32d21-117">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="32d21-118">Použití asynchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="32d21-118">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="32d21-119">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="32d21-119">Using Application Protocols</span></span>](using-application-protocols.md)
