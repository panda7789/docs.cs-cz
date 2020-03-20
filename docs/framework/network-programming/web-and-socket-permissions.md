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
ms.openlocfilehash: d1b993acbf20eac244e596075c3f826bba3211a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71046869"
---
# <a name="web-and-socket-permissions"></a><span data-ttu-id="52e36-102">Oprávnění pro web a sokety</span><span class="sxs-lookup"><span data-stu-id="52e36-102">Web and Socket Permissions</span></span>
<span data-ttu-id="52e36-103">Zabezpečení Internetu pro <xref:System.Net> aplikace používající obor <xref:System.Net.WebPermission> názvů <xref:System.Net.SocketPermission> je poskytováno třídami a.</span><span class="sxs-lookup"><span data-stu-id="52e36-103">Internet security for applications using the <xref:System.Net> namespace is provided by the <xref:System.Net.WebPermission> and <xref:System.Net.SocketPermission> classes.</span></span> <span data-ttu-id="52e36-104">Třída **WebPermission** řídí právo aplikace požadovat data z identifikátoru URI nebo obsluhovat identifikátor URI v Síti Internet.</span><span class="sxs-lookup"><span data-stu-id="52e36-104">The **WebPermission** class controls an application's right to request data from a URI or to serve a URI to the Internet.</span></span> <span data-ttu-id="52e36-105">Třída **SocketPermission** řídí právo aplikace používat <xref:System.Net.Sockets.Socket> a přijímat data na místním portu nebo kontaktovat vzdálená zařízení pomocí přenosového protokolu na jiné adrese na základě hostitele, čísla portu a přenosového protokolu soketu.</span><span class="sxs-lookup"><span data-stu-id="52e36-105">The **SocketPermission** class controls an application's right to use a <xref:System.Net.Sockets.Socket> to accept data on a local port or to contact remote devices using a transport protocol at another address, based on the host, port number, and transport protocol of the socket.</span></span>  
  
 <span data-ttu-id="52e36-106">Třída oprávnění, kterou používáte, závisí na typu aplikace.</span><span class="sxs-lookup"><span data-stu-id="52e36-106">Which permission class you use depends on your application type.</span></span> <span data-ttu-id="52e36-107">Aplikace, <xref:System.Net.WebRequest> které používají a jeho následníky by měly používat **WebPermission** třídy ke správě oprávnění.</span><span class="sxs-lookup"><span data-stu-id="52e36-107">Applications that use <xref:System.Net.WebRequest> and its descendants should use the **WebPermission** class to manage permissions.</span></span> <span data-ttu-id="52e36-108">Aplikace, které používají přístup na úrovni soketu, by měly ke správě oprávnění používat třídu **SocketPermission.**</span><span class="sxs-lookup"><span data-stu-id="52e36-108">Applications that use socket-level access should use the **SocketPermission** class to manage permissions.</span></span>  
  
 <span data-ttu-id="52e36-109">**WebPermission** a **SocketPermission** definovat dvě oprávnění: přijmout a připojit.</span><span class="sxs-lookup"><span data-stu-id="52e36-109">**WebPermission** and **SocketPermission** define two permissions: accept and connect.</span></span> <span data-ttu-id="52e36-110">Přijmout uděluje aplikaci právo odpovědět na příchozí připojení od jiné strany.</span><span class="sxs-lookup"><span data-stu-id="52e36-110">Accept grants the application the right to answer an incoming connection from another party.</span></span> <span data-ttu-id="52e36-111">Connect uděluje aplikaci právo nazatouji připojení k jiné straně.</span><span class="sxs-lookup"><span data-stu-id="52e36-111">Connect grants the application the right to initiate a connection to another party.</span></span>  
  
 <span data-ttu-id="52e36-112">Pro **SocketPermission** instance, přijmout znamená, že aplikace může přijímat příchozí připojení na adresu místního přenosu; znamená, že se aplikace může připojit k některé vzdálené (nebo místní) adrese přenosu.</span><span class="sxs-lookup"><span data-stu-id="52e36-112">For **SocketPermission** instances, accept means that an application can accept incoming connections on a local transport address; connect means that an application can connect to some remote (or local) transport address.</span></span>  
  
 <span data-ttu-id="52e36-113">Pro instance **WebPermission,** přijmout znamená, že aplikace může exportovat identifikátor URI řízené **WebPermission** do světa; znamená, že aplikace může přistupovat k tomuto identifikátoru URI (ať už je vzdálený nebo místní).</span><span class="sxs-lookup"><span data-stu-id="52e36-113">For **WebPermission** instances, accept means that an application can export the URI controlled by the **WebPermission** to the world; connect means that an application can access that URI (whether it is remote or local).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52e36-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="52e36-114">See also</span></span>

- [<span data-ttu-id="52e36-115">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="52e36-115">Security</span></span>](../../standard/security/index.md)
- [<span data-ttu-id="52e36-116">Zabezpečení v síťovém programování</span><span class="sxs-lookup"><span data-stu-id="52e36-116">Security in Network Programming</span></span>](security-in-network-programming.md)
