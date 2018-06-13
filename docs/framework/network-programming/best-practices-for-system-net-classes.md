---
title: Osvědčené postupy pro System.NET – třídy
ms.date: 03/30/2017
helpviewer_keywords:
- sending data, best practices
- requesting data from Internet, best practices
- WebRequest class, best practices
- data requests, best practices
- WebResponse class, best practices
- best practices, data requests
- receiving data, best practices
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c74f9d0534675d07c87d3edbcf8434cd98f6c621
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393942"
---
# <a name="best-practices-for-systemnet-classes"></a><span data-ttu-id="8a7ec-102">Osvědčené postupy pro System.NET – třídy</span><span class="sxs-lookup"><span data-stu-id="8a7ec-102">Best Practices for System.Net Classes</span></span>
<span data-ttu-id="8a7ec-103">Následující doporučení vám pomůže používat třídy součástí <xref:System.Net> využívají doporučené:</span><span class="sxs-lookup"><span data-stu-id="8a7ec-103">The following recommendations will help you use the classes contained in <xref:System.Net> to their best advantage:</span></span>  
  
-   <span data-ttu-id="8a7ec-104">Osvědčené postupy zabezpečení TLS (Transport Layer), najdete v části [zabezpečení TLS (Transport Layer) osvědčené postupy v rozhraní .NET Framework](tls.md).</span><span class="sxs-lookup"><span data-stu-id="8a7ec-104">For Transport Layer Security (TLS) best practices, see [Transport Layer Security (TLS) best practices with .NET Framework](tls.md).</span></span>

-   <span data-ttu-id="8a7ec-105">Použití <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> kdykoli je to možné místo přetypování typu do odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="8a7ec-105">Use <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> whenever possible instead of type casting to descendant classes.</span></span> <span data-ttu-id="8a7ec-106">Aplikace, které používají **WebRequest** a **WebResponse** můžete využít výhod nové protokoly Internetu bez nutnosti změny rozsáhlé kódu.</span><span class="sxs-lookup"><span data-stu-id="8a7ec-106">Applications that use **WebRequest** and **WebResponse** can take advantage of new Internet protocols without needing extensive code changes.</span></span>  
  
-   <span data-ttu-id="8a7ec-107">Při vytváření aplikací ASP.NET, které běží na serveru pomocí **System.Net** třídy, je často lepší, z hlediska výkonu použít asynchronní metody pro <xref:System.Net.WebRequest.GetResponse%2A> a <xref:System.Net.WebResponse.GetResponseStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="8a7ec-107">When writing ASP.NET applications that run on a server using the **System.Net** classes, it is often better, from a performance standpoint, to use the asynchronous methods for <xref:System.Net.WebRequest.GetResponse%2A> and <xref:System.Net.WebResponse.GetResponseStream%2A>.</span></span>  
  
-   <span data-ttu-id="8a7ec-108">Počet otevřených připojení k internetového zdroji může mít významný dopad na výkon sítě a propustnosti.</span><span class="sxs-lookup"><span data-stu-id="8a7ec-108">The number of connections opened to an Internet resource can have a significant impact on network performance and throughput.</span></span> <span data-ttu-id="8a7ec-109">**System.Net** používá dvě připojení na aplikaci na hostitele ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="8a7ec-109">**System.Net** uses two connections per application per host by default.</span></span> <span data-ttu-id="8a7ec-110">Nastavení <xref:System.Net.ServicePoint.ConnectionLimit%2A> vlastnost <xref:System.Net.ServicePoint> pro aplikaci můžete tento počet zvýšit pro konkrétního hostitele.</span><span class="sxs-lookup"><span data-stu-id="8a7ec-110">Setting the <xref:System.Net.ServicePoint.ConnectionLimit%2A> property in the <xref:System.Net.ServicePoint> for your application can increase this number for a particular host.</span></span> <span data-ttu-id="8a7ec-111">Nastavení <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> vlastnost může prodloužit toto výchozí nastavení pro všechny hostitele.</span><span class="sxs-lookup"><span data-stu-id="8a7ec-111">Setting the <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> property can increase this default for all hosts.</span></span>  
  
-   <span data-ttu-id="8a7ec-112">Při zápisu úrovni soketu protokoly, zkuste použít <xref:System.Net.Sockets.TcpClient> nebo <xref:System.Net.Sockets.UdpClient> kdykoli je to možné místo přímo na zápis <xref:System.Net.Sockets.Socket>.</span><span class="sxs-lookup"><span data-stu-id="8a7ec-112">When writing socket-level protocols, try to use <xref:System.Net.Sockets.TcpClient> or <xref:System.Net.Sockets.UdpClient> whenever possible instead of writing directly to a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="8a7ec-113">Tyto dva klientské třídy zapouzdřovat vytvoření TCP a UDP soketů aniž by bylo potřeba zpracovávají údaje o připojení.</span><span class="sxs-lookup"><span data-stu-id="8a7ec-113">These two client classes encapsulate the creation of TCP and UDP sockets without requiring you to handle the details of the connection.</span></span>  
  
-   <span data-ttu-id="8a7ec-114">Při přístupu k webům, které vyžadují přihlašovací údaje, použijte <xref:System.Net.CredentialCache> třídy za účelem vytvoření mezipaměti přihlašovací údaje místo zadávání je s každou žádostí.</span><span class="sxs-lookup"><span data-stu-id="8a7ec-114">When accessing sites that require credentials, use the <xref:System.Net.CredentialCache> class to create a cache of credentials rather than supplying them with every request.</span></span> <span data-ttu-id="8a7ec-115">**CredentialCache** třída vyhledá mezipaměti najít odpovídající přihlašovací údaje k dispozici s žádostí, můžete kerberosu zodpovědnosti při vytváření a prezentování přihlašovací údaje založené na adresu URL.</span><span class="sxs-lookup"><span data-stu-id="8a7ec-115">The **CredentialCache** class searches the cache to find the appropriate credential to present with a request, relieving you of the responsibility of creating and presenting credentials based on the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a7ec-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="8a7ec-116">See Also</span></span>  
 [<span data-ttu-id="8a7ec-117">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8a7ec-117">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)
