---
title: TCP-UDP
description: Přečtěte si, jak třídy TcpClient, třída TcpListener nesmí a UdpClient zpracovávají služby TCP a UDP, které pobírají podrobnosti přenosu dat v .NET Framework.
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
ms.openlocfilehash: ae6d2f9ced2235aa1b9b8fada8064d7e4be970a0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502090"
---
# <a name="tcp-udp"></a><span data-ttu-id="a4b08-103">TCP-UDP</span><span class="sxs-lookup"><span data-stu-id="a4b08-103">TCP-UDP</span></span>
<span data-ttu-id="a4b08-104">Aplikace mohou používat služby protokolu TCP (Transmission Control Protocol) a UDP (User Datagram Protocol) s <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Sockets.TcpListener> <xref:System.Net.Sockets.UdpClient> třídami, a.</span><span class="sxs-lookup"><span data-stu-id="a4b08-104">Applications can use Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) services with the <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes.</span></span> <span data-ttu-id="a4b08-105">Tyto třídy protokolu jsou postaveny nad <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> třídou a postarou se o podrobnosti přenosu dat.</span><span class="sxs-lookup"><span data-stu-id="a4b08-105">These protocol classes are built on top of the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class and take care of the details of transferring data.</span></span>  
  
 <span data-ttu-id="a4b08-106">Třídy protokolu používají synchronní metody třídy **Socket** k poskytování jednoduchého a jednoduššího přístupu k síťovým službám bez režie údržby stavových informací nebo zjištění podrobností o nastavení soketů specifických pro protokol.</span><span class="sxs-lookup"><span data-stu-id="a4b08-106">The protocol classes use the synchronous methods of the **Socket** class to provide simple and straightforward access to network services without the overhead of maintaining state information or knowing the details of setting up protocol-specific sockets.</span></span> <span data-ttu-id="a4b08-107">Chcete-li použít metody asynchronního **soketu** , můžete použít asynchronní metody poskytované <xref:System.Net.Sockets.NetworkStream> třídou.</span><span class="sxs-lookup"><span data-stu-id="a4b08-107">To use asynchronous **Socket** methods, you can use the asynchronous methods supplied by the <xref:System.Net.Sockets.NetworkStream> class.</span></span> <span data-ttu-id="a4b08-108">Chcete-li získat přístup k funkcím třídy **Socket** , která není vystavena třídami protokolu, je nutné použít třídu **Socket** .</span><span class="sxs-lookup"><span data-stu-id="a4b08-108">To access features of the **Socket** class not exposed by the protocol classes, you must use the **Socket** class.</span></span>  
  
 <span data-ttu-id="a4b08-109">**TcpClient** a **Třída TcpListener nesmí** reprezentují síť pomocí třídy **NetworkStream** .</span><span class="sxs-lookup"><span data-stu-id="a4b08-109">**TcpClient** and **TcpListener** represent the network using the **NetworkStream** class.</span></span> <span data-ttu-id="a4b08-110">Použijte <xref:System.Net.Sockets.TcpClient.GetStream%2A> metodu k vrácení síťového datového proudu a pak zavolejte <xref:System.Net.Sockets.NetworkStream.Read%2A> <xref:System.Net.Sockets.NetworkStream.Write%2A> metody a.</span><span class="sxs-lookup"><span data-stu-id="a4b08-110">You use the <xref:System.Net.Sockets.TcpClient.GetStream%2A> method to return the network stream, and then call the stream's <xref:System.Net.Sockets.NetworkStream.Read%2A> and <xref:System.Net.Sockets.NetworkStream.Write%2A> methods.</span></span> <span data-ttu-id="a4b08-111">**NetworkStream** nevlastní základní soket tříd protokolů, takže jeho zavření nemá vliv na soket.</span><span class="sxs-lookup"><span data-stu-id="a4b08-111">The **NetworkStream** does not own the protocol classes' underlying socket, so closing it does not affect the socket.</span></span>  
  
 <span data-ttu-id="a4b08-112">Třída **UdpClient** používá pole bajtů k uložení datagramu UDP.</span><span class="sxs-lookup"><span data-stu-id="a4b08-112">The **UdpClient** class uses an array of bytes to hold the UDP datagram.</span></span> <span data-ttu-id="a4b08-113">Použijte <xref:System.Net.Sockets.UdpClient.Send%2A> metodu k odeslání dat do sítě a <xref:System.Net.Sockets.UdpClient.Receive%2A> metody pro příjem příchozího datagramu.</span><span class="sxs-lookup"><span data-stu-id="a4b08-113">You use the <xref:System.Net.Sockets.UdpClient.Send%2A> method to send the data to the network and the <xref:System.Net.Sockets.UdpClient.Receive%2A> method to receive an incoming datagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4b08-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4b08-114">See also</span></span>

- [<span data-ttu-id="a4b08-115">Použití služeb TCP</span><span class="sxs-lookup"><span data-stu-id="a4b08-115">Using TCP Services</span></span>](using-tcp-services.md)
- [<span data-ttu-id="a4b08-116">Použití služeb UDP</span><span class="sxs-lookup"><span data-stu-id="a4b08-116">Using UDP Services</span></span>](using-udp-services.md)
- [<span data-ttu-id="a4b08-117">Použití streamů v síti</span><span class="sxs-lookup"><span data-stu-id="a4b08-117">Using Streams on the Network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="a4b08-118">Použití asynchronního serverového soketu</span><span class="sxs-lookup"><span data-stu-id="a4b08-118">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="a4b08-119">Použití asynchronního klientského soketu</span><span class="sxs-lookup"><span data-stu-id="a4b08-119">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="a4b08-120">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="a4b08-120">Using Application Protocols</span></span>](using-application-protocols.md)
