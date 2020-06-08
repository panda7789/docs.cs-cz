---
title: 'Postupy: Vytvoření soketu'
description: Naučte se inicializovat soket ke komunikaci se vzdálenými zařízeními. Pomocí třídy Socket můžete určit rodinu adres, typ soketu a typ protokolu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- Networking
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- Socket class, creating sockets
- Network Resources
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- sockets, creating
ms.assetid: c64a049c-5981-43bc-a2dc-1851473589c7
ms.openlocfilehash: 1d56ddea721b54192a7dd47d144b6c41bbb9a5d7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502545"
---
# <a name="how-to-create-a-socket"></a><span data-ttu-id="7583e-104">Postupy: Vytvoření soketu</span><span class="sxs-lookup"><span data-stu-id="7583e-104">How to: Create a Socket</span></span>
<span data-ttu-id="7583e-105">Předtím, než budete moci použít soket ke komunikaci se vzdálenými zařízeními, je nutné soket inicializovat pomocí informací o protokolu a síťové adrese.</span><span class="sxs-lookup"><span data-stu-id="7583e-105">Before you can use a socket to communicate with remote devices, the socket must be initialized with protocol and network address information.</span></span> <span data-ttu-id="7583e-106">Konstruktor <xref:System.Net.Sockets.Socket> třídy má parametry, které určují rodinu adres, typ soketu a typ protokolu, který soket používá k vytváření připojení.</span><span class="sxs-lookup"><span data-stu-id="7583e-106">The constructor for the <xref:System.Net.Sockets.Socket> class has parameters that specify the address family, socket type, and protocol type that the socket uses to make connections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7583e-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="7583e-107">Example</span></span>  
 <span data-ttu-id="7583e-108">Následující příklad vytvoří soket, který lze použít ke komunikaci v síti založené na protokolu TCP/IP, jako je například Internet.</span><span class="sxs-lookup"><span data-stu-id="7583e-108">The following example creates a Socket that can be used to communicate on a TCP/IP-based network, such as the Internet.</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 <span data-ttu-id="7583e-109">Pokud chcete místo TCP používat protokol UDP, změňte typ protokolu tak, jak je uvedeno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="7583e-109">To use UDP instead of TCP, change the protocol type, as in the following example:</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <span data-ttu-id="7583e-110"><xref:System.Net.Sockets.AddressFamily>Výčet Určuje standardní skupiny adres používané třídou **Socket** k překladu síťových adres (například člen **parametr AddressFamily. INTERNETWORK** Určuje rodinu adres IP verze 4).</span><span class="sxs-lookup"><span data-stu-id="7583e-110">The <xref:System.Net.Sockets.AddressFamily> enumeration specifies the standard address families used by the **Socket** class to resolve network addresses (for example, the **AddressFamily.InterNetwork** member specifies the IP version 4 address family).</span></span>  
  
 <span data-ttu-id="7583e-111"><xref:System.Net.Sockets.SocketType>Výčet Určuje typ soketu (například člen **SocketType. Stream** indikuje standardní soket pro odesílání a příjem dat pomocí řízení toku).</span><span class="sxs-lookup"><span data-stu-id="7583e-111">The <xref:System.Net.Sockets.SocketType> enumeration specifies the type of socket (for example, the **SocketType.Stream** member indicates a standard socket for sending and receiving data with flow control).</span></span>  
  
 <span data-ttu-id="7583e-112"><xref:System.Net.Sockets.ProtocolType>Výčet Určuje síťový protokol, který se má použít při komunikaci na **soketu** (například **typprotokolu. TCP** znamená, že soket používá protokol TCP; **Typprotokolu. UDP** označuje, že SOKET používá UDP).</span><span class="sxs-lookup"><span data-stu-id="7583e-112">The <xref:System.Net.Sockets.ProtocolType> enumeration specifies the network protocol to use when communicating on the **Socket** (for example, **ProtocolType.Tcp** indicates that the socket uses TCP; **ProtocolType.Udp** indicates that the socket uses UDP).</span></span>  
  
 <span data-ttu-id="7583e-113">Po vytvoření **soketu** může buď iniciovat připojení ke vzdálenému koncovému bodu, nebo přijímat připojení ze vzdálených zařízení.</span><span class="sxs-lookup"><span data-stu-id="7583e-113">After a **Socket** is created, it can either initiate a connection to a remote endpoint or receive connections from remote devices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7583e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7583e-114">See also</span></span>

- [<span data-ttu-id="7583e-115">Použití klientských soketů</span><span class="sxs-lookup"><span data-stu-id="7583e-115">Using Client Sockets</span></span>](using-client-sockets.md)
- [<span data-ttu-id="7583e-116">Naslouchání pomocí soketů</span><span class="sxs-lookup"><span data-stu-id="7583e-116">Listening with Sockets</span></span>](listening-with-sockets.md)
