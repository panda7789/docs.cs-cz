---
title: Oprávnění pro web a sokety
description: Přečtěte si, jak třídy weboprávnění a SocketPermission poskytují zabezpečení Internetu pro používání oboru názvů System.Net v .NET Framework.
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- positions [.NET Framework], accepting
- sockets, permissions
- network, permissions
- Internet, permissions
- Network Resources
- SocketPermission class, about SocketPermission class
- positions [.NET Framework], connecting
- WebPermission class, about WebPermission class
- permissions [.NET Framework], sockets
- security [.NET Framework], Internet
- positions [.NET Framework], granting
ms.assetid: d51ad8cb-03ae-4a51-bfcd-cfcf6b98afa9
ms.openlocfilehash: 08ae360e8097f7281631da2a3f9846994dfbf5b6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501895"
---
# <a name="web-and-socket-permissions"></a><span data-ttu-id="ddd1a-103">Oprávnění pro web a sokety</span><span class="sxs-lookup"><span data-stu-id="ddd1a-103">Web and Socket Permissions</span></span>
<span data-ttu-id="ddd1a-104">Internetové zabezpečení pro aplikace, které používají <xref:System.Net> obor názvů, jsou <xref:System.Net.WebPermission> poskytovány <xref:System.Net.SocketPermission> třídami a.</span><span class="sxs-lookup"><span data-stu-id="ddd1a-104">Internet security for applications using the <xref:System.Net> namespace is provided by the <xref:System.Net.WebPermission> and <xref:System.Net.SocketPermission> classes.</span></span> <span data-ttu-id="ddd1a-105">Třída **weboprávnění** řídí právo aplikace pro vyžádání dat z identifikátoru URI nebo pro poskytování identifikátoru URI Internetu.</span><span class="sxs-lookup"><span data-stu-id="ddd1a-105">The **WebPermission** class controls an application's right to request data from a URI or to serve a URI to the Internet.</span></span> <span data-ttu-id="ddd1a-106">Třída **SocketPermission** řídí právo aplikace používat <xref:System.Net.Sockets.Socket> k přijímání dat na místním portu nebo ke kontaktování vzdálených zařízení pomocí přenosového protokolu na jiné adrese, a to na základě hostitele, čísla portu a přenosového protokolu soketu.</span><span class="sxs-lookup"><span data-stu-id="ddd1a-106">The **SocketPermission** class controls an application's right to use a <xref:System.Net.Sockets.Socket> to accept data on a local port or to contact remote devices using a transport protocol at another address, based on the host, port number, and transport protocol of the socket.</span></span>  
  
 <span data-ttu-id="ddd1a-107">Použitá třída oprávnění závisí na typu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="ddd1a-107">Which permission class you use depends on your application type.</span></span> <span data-ttu-id="ddd1a-108">Aplikace, které používají <xref:System.Net.WebRequest> a její potomci, by měli použít třídu **weboprávnění** ke správě oprávnění.</span><span class="sxs-lookup"><span data-stu-id="ddd1a-108">Applications that use <xref:System.Net.WebRequest> and its descendants should use the **WebPermission** class to manage permissions.</span></span> <span data-ttu-id="ddd1a-109">Aplikace, které používají přístup na úrovni soketu, by měly ke správě oprávnění používat třídu **SocketPermission** .</span><span class="sxs-lookup"><span data-stu-id="ddd1a-109">Applications that use socket-level access should use the **SocketPermission** class to manage permissions.</span></span>  
  
 <span data-ttu-id="ddd1a-110">**Weboprávnění** a **SocketPermission** definují dvě oprávnění: přijmout a připojit.</span><span class="sxs-lookup"><span data-stu-id="ddd1a-110">**WebPermission** and **SocketPermission** define two permissions: accept and connect.</span></span> <span data-ttu-id="ddd1a-111">Accept udělí aplikaci právo odpovědět příchozímu připojení z jiné strany.</span><span class="sxs-lookup"><span data-stu-id="ddd1a-111">Accept grants the application the right to answer an incoming connection from another party.</span></span> <span data-ttu-id="ddd1a-112">Připojení uděluje aplikaci právo iniciovat připojení k jiné straně.</span><span class="sxs-lookup"><span data-stu-id="ddd1a-112">Connect grants the application the right to initiate a connection to another party.</span></span>  
  
 <span data-ttu-id="ddd1a-113">U instancí **SocketPermission** Accept (přijmout) znamená, že aplikace může přijmout příchozí připojení na místní transportní adrese; připojit znamená, že se aplikace může připojit k některé vzdálené (nebo místní) transportní adrese.</span><span class="sxs-lookup"><span data-stu-id="ddd1a-113">For **SocketPermission** instances, accept means that an application can accept incoming connections on a local transport address; connect means that an application can connect to some remote (or local) transport address.</span></span>  
  
 <span data-ttu-id="ddd1a-114">U instancí **weboprávnění** Accept (přijmout) znamená, že aplikace může exportovat identifikátor URI řízený **weboprávněními** na světě; možnost připojit znamená, že aplikace má přístup k tomuto identifikátoru URI (ať už se jedná o vzdálené nebo místní).</span><span class="sxs-lookup"><span data-stu-id="ddd1a-114">For **WebPermission** instances, accept means that an application can export the URI controlled by the **WebPermission** to the world; connect means that an application can access that URI (whether it is remote or local).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddd1a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ddd1a-115">See also</span></span>

- [<span data-ttu-id="ddd1a-116">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ddd1a-116">Security</span></span>](../../standard/security/index.md)
- [<span data-ttu-id="ddd1a-117">Zabezpečení v síťovém programování</span><span class="sxs-lookup"><span data-stu-id="ddd1a-117">Security in Network Programming</span></span>](security-in-network-programming.md)
