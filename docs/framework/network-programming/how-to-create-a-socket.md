---
title: 'Postupy: vytvoření soketu'
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 2ec87d45a4e7140aa2c1d901492952cd25634025
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47192214"
---
# <a name="how-to-create-a-socket"></a><span data-ttu-id="e0ac9-102">Postupy: vytvoření soketu</span><span class="sxs-lookup"><span data-stu-id="e0ac9-102">How to: Create a Socket</span></span>
<span data-ttu-id="e0ac9-103">Než použijete soket pro komunikaci se vzdálenými zařízeními soketu. je nutné inicializovat s informace o protokolu a síťové adrese.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-103">Before you can use a socket to communicate with remote devices, the socket must be initialized with protocol and network address information.</span></span> <span data-ttu-id="e0ac9-104">Konstruktor pro <xref:System.Net.Sockets.Socket> třída obsahuje parametry, které určují rodina adres, typ soketu a typ protokolu, který využívá soket, aby připojení.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-104">The constructor for the <xref:System.Net.Sockets.Socket> class has parameters that specify the address family, socket type, and protocol type that the socket uses to make connections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0ac9-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0ac9-105">Example</span></span>  
 <span data-ttu-id="e0ac9-106">Následující příklad vytvoří soket, který slouží ke komunikaci v síti založené na TCP/IP, jako je Internet.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-106">The following example creates a Socket that can be used to communicate on a TCP/IP-based network, such as the Internet.</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 <span data-ttu-id="e0ac9-107">Místo TCP použít UDP, změňte typ protokolu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e0ac9-107">To use UDP instead of TCP, change the protocol type, as in the following example:</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <span data-ttu-id="e0ac9-108"><xref:System.Net.Sockets.AddressFamily> Výčet určuje rodiny standardní adres používané **soketu** třídy vyřešit síťových adres (například **AddressFamily.InterNetwork** člen Určuje IP adresu Rodina adres verze 4).</span><span class="sxs-lookup"><span data-stu-id="e0ac9-108">The <xref:System.Net.Sockets.AddressFamily> enumeration specifies the standard address families used by the **Socket** class to resolve network addresses (for example, the **AddressFamily.InterNetwork** member specifies the IP version 4 address family).</span></span>  
  
 <span data-ttu-id="e0ac9-109"><xref:System.Net.Sockets.SocketType> Výčet Určuje typ soketu (například **SocketType.Stream** člen označuje standardní soket pro odesílání a přijímání dat pomocí toku řízení).</span><span class="sxs-lookup"><span data-stu-id="e0ac9-109">The <xref:System.Net.Sockets.SocketType> enumeration specifies the type of socket (for example, the **SocketType.Stream** member indicates a standard socket for sending and receiving data with flow control).</span></span>  
  
 <span data-ttu-id="e0ac9-110"><xref:System.Net.Sockets.ProtocolType> Výčet Určuje protokol sítě při komunikaci na **soketu** (například **ProtocolType.Tcp** označuje, že používá soket TCP; **ProtocolType.Udp** označuje, že soketu používá UDP).</span><span class="sxs-lookup"><span data-stu-id="e0ac9-110">The <xref:System.Net.Sockets.ProtocolType> enumeration specifies the network protocol to use when communicating on the **Socket** (for example, **ProtocolType.Tcp** indicates that the socket uses TCP; **ProtocolType.Udp** indicates that the socket uses UDP).</span></span>  
  
 <span data-ttu-id="e0ac9-111">Po **soketu** je vytvořen, ho můžete inicializovat připojení a vzdálený koncový bod nebo přijímat připojení ze vzdálených zařízeních.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-111">After a **Socket** is created, it can either initiate a connection to a remote endpoint or receive connections from remote devices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0ac9-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0ac9-112">See Also</span></span>  
 [<span data-ttu-id="e0ac9-113">Použití klientských soketů</span><span class="sxs-lookup"><span data-stu-id="e0ac9-113">Using Client Sockets</span></span>](../../../docs/framework/network-programming/using-client-sockets.md)  
 [<span data-ttu-id="e0ac9-114">Naslouchání pomocí soketů</span><span class="sxs-lookup"><span data-stu-id="e0ac9-114">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
