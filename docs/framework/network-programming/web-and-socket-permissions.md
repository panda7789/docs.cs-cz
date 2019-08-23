---
title: Oprávnění pro web a sokety
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
ms.openlocfilehash: fbb4e5d7171c50c06f55706df90240ffa205ee73
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967624"
---
# <a name="web-and-socket-permissions"></a><span data-ttu-id="33306-102">Oprávnění pro web a sokety</span><span class="sxs-lookup"><span data-stu-id="33306-102">Web and Socket Permissions</span></span>
<span data-ttu-id="33306-103">Internetové zabezpečení pro aplikace, které <xref:System.Net> používají obor názvů, jsou <xref:System.Net.WebPermission> poskytovány <xref:System.Net.SocketPermission> třídami a.</span><span class="sxs-lookup"><span data-stu-id="33306-103">Internet security for applications using the <xref:System.Net> namespace is provided by the <xref:System.Net.WebPermission> and <xref:System.Net.SocketPermission> classes.</span></span> <span data-ttu-id="33306-104">Třída **weboprávnění** řídí právo aplikace pro vyžádání dat z identifikátoru URI nebo pro poskytování identifikátoru URI Internetu.</span><span class="sxs-lookup"><span data-stu-id="33306-104">The **WebPermission** class controls an application's right to request data from a URI or to serve a URI to the Internet.</span></span> <span data-ttu-id="33306-105">Třída **SocketPermission** řídí právo aplikace používat <xref:System.Net.Sockets.Socket> k přijímání dat na místním portu nebo ke kontaktování vzdálených zařízení pomocí přenosového protokolu na jiné adrese, a to na základě hostitele, čísla portu a přenosového protokolu. zásuvky.</span><span class="sxs-lookup"><span data-stu-id="33306-105">The **SocketPermission** class controls an application's right to use a <xref:System.Net.Sockets.Socket> to accept data on a local port or to contact remote devices using a transport protocol at another address, based on the host, port number, and transport protocol of the socket.</span></span>  
  
 <span data-ttu-id="33306-106">Použitá třída oprávnění závisí na typu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="33306-106">Which permission class you use depends on your application type.</span></span> <span data-ttu-id="33306-107">Aplikace, které <xref:System.Net.WebRequest> používají a její potomci, by měli použít třídu weboprávnění ke správě oprávnění.</span><span class="sxs-lookup"><span data-stu-id="33306-107">Applications that use <xref:System.Net.WebRequest> and its descendants should use the **WebPermission** class to manage permissions.</span></span> <span data-ttu-id="33306-108">Aplikace, které používají přístup na úrovni soketu, by měly ke správě oprávnění používat třídu **SocketPermission** .</span><span class="sxs-lookup"><span data-stu-id="33306-108">Applications that use socket-level access should use the **SocketPermission** class to manage permissions.</span></span>  
  
 <span data-ttu-id="33306-109">**Weboprávnění** a **SocketPermission** definují dvě oprávnění: přijmout a připojit.</span><span class="sxs-lookup"><span data-stu-id="33306-109">**WebPermission** and **SocketPermission** define two permissions: accept and connect.</span></span> <span data-ttu-id="33306-110">Accept udělí aplikaci právo odpovědět příchozímu připojení z jiné strany.</span><span class="sxs-lookup"><span data-stu-id="33306-110">Accept grants the application the right to answer an incoming connection from another party.</span></span> <span data-ttu-id="33306-111">Připojení uděluje aplikaci právo iniciovat připojení k jiné straně.</span><span class="sxs-lookup"><span data-stu-id="33306-111">Connect grants the application the right to initiate a connection to another party.</span></span>  
  
 <span data-ttu-id="33306-112">U instancí **SocketPermission** Accept (přijmout) znamená, že aplikace může přijmout příchozí připojení na místní transportní adrese; připojit znamená, že se aplikace může připojit k některé vzdálené (nebo místní) transportní adrese.</span><span class="sxs-lookup"><span data-stu-id="33306-112">For **SocketPermission** instances, accept means that an application can accept incoming connections on a local transport address; connect means that an application can connect to some remote (or local) transport address.</span></span>  
  
 <span data-ttu-id="33306-113">U instancí weboprávnění Accept (přijmout) znamená, že aplikace může exportovat identifikátor URI řízený **weboprávněními** na světě; možnost připojit znamená, že aplikace má přístup k tomuto identifikátoru URI (ať už se jedná o vzdálené nebo místní).</span><span class="sxs-lookup"><span data-stu-id="33306-113">For **WebPermission** instances, accept means that an application can export the URI controlled by the **WebPermission** to the world; connect means that an application can access that URI (whether it is remote or local).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33306-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="33306-114">See also</span></span>

- [<span data-ttu-id="33306-115">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="33306-115">Security</span></span>](../../standard/security/index.md)
- [<span data-ttu-id="33306-116">Zabezpečení v síťovém programování</span><span class="sxs-lookup"><span data-stu-id="33306-116">Security in Network Programming</span></span>](../../../docs/framework/network-programming/security-in-network-programming.md)
