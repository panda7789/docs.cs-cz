---
title: "Osvědčené postupy pro System.NET – třídy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sending data, best practices
- requesting data from Internet, best practices
- WebRequest class, best practices
- data requests, best practices
- WebResponse class, best practices
- best practices, data requests
- receiving data, best practices
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e50df22f66d4d55298aad5f3cc501dfb39ffcd9a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="best-practices-for-systemnet-classes"></a><span data-ttu-id="cb29c-102">Osvědčené postupy pro System.NET – třídy</span><span class="sxs-lookup"><span data-stu-id="cb29c-102">Best Practices for System.Net Classes</span></span>
<span data-ttu-id="cb29c-103">Následující doporučení vám pomůže používat třídy součástí <xref:System.Net> využívají doporučené:</span><span class="sxs-lookup"><span data-stu-id="cb29c-103">The following recommendations will help you use the classes contained in <xref:System.Net> to their best advantage:</span></span>  
  
-   <span data-ttu-id="cb29c-104">Použití <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> kdykoli je to možné místo přetypování typu do odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="cb29c-104">Use <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> whenever possible instead of type casting to descendant classes.</span></span> <span data-ttu-id="cb29c-105">Aplikace, které používají **WebRequest** a **WebResponse** můžete využít výhod nové protokoly Internetu bez nutnosti změny rozsáhlé kódu.</span><span class="sxs-lookup"><span data-stu-id="cb29c-105">Applications that use **WebRequest** and **WebResponse** can take advantage of new Internet protocols without needing extensive code changes.</span></span>  
  
-   <span data-ttu-id="cb29c-106">Při vytváření aplikací ASP.NET, které běží na serveru pomocí **System.Net** třídy, je často lepší, z hlediska výkonu použít asynchronní metody pro <xref:System.Net.WebRequest.GetResponse%2A> a <xref:System.Net.WebResponse.GetResponseStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="cb29c-106">When writing ASP.NET applications that run on a server using the **System.Net** classes, it is often better, from a performance standpoint, to use the asynchronous methods for <xref:System.Net.WebRequest.GetResponse%2A> and <xref:System.Net.WebResponse.GetResponseStream%2A>.</span></span>  
  
-   <span data-ttu-id="cb29c-107">Počet otevřených připojení k internetového zdroji může mít významný dopad na výkon sítě a propustnosti.</span><span class="sxs-lookup"><span data-stu-id="cb29c-107">The number of connections opened to an Internet resource can have a significant impact on network performance and throughput.</span></span> <span data-ttu-id="cb29c-108">**System.Net** používá dvě připojení na aplikaci na hostitele ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="cb29c-108">**System.Net** uses two connections per application per host by default.</span></span> <span data-ttu-id="cb29c-109">Nastavení <xref:System.Net.ServicePoint.ConnectionLimit%2A> vlastnost <xref:System.Net.ServicePoint> pro aplikaci můžete tento počet zvýšit pro konkrétního hostitele.</span><span class="sxs-lookup"><span data-stu-id="cb29c-109">Setting the <xref:System.Net.ServicePoint.ConnectionLimit%2A> property in the <xref:System.Net.ServicePoint> for your application can increase this number for a particular host.</span></span> <span data-ttu-id="cb29c-110">Nastavení <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> vlastnost může prodloužit toto výchozí nastavení pro všechny hostitele.</span><span class="sxs-lookup"><span data-stu-id="cb29c-110">Setting the <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> property can increase this default for all hosts.</span></span>  
  
-   <span data-ttu-id="cb29c-111">Při zápisu úrovni soketu protokoly, zkuste použít <xref:System.Net.Sockets.TcpClient> nebo <xref:System.Net.Sockets.UdpClient> kdykoli je to možné místo přímo na zápis <xref:System.Net.Sockets.Socket>.</span><span class="sxs-lookup"><span data-stu-id="cb29c-111">When writing socket-level protocols, try to use <xref:System.Net.Sockets.TcpClient> or <xref:System.Net.Sockets.UdpClient> whenever possible instead of writing directly to a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="cb29c-112">Tyto dva klientské třídy zapouzdřovat vytvoření TCP a UDP soketů aniž by bylo potřeba zpracovávají údaje o připojení.</span><span class="sxs-lookup"><span data-stu-id="cb29c-112">These two client classes encapsulate the creation of TCP and UDP sockets without requiring you to handle the details of the connection.</span></span>  
  
-   <span data-ttu-id="cb29c-113">Při přístupu k webům, které vyžadují přihlašovací údaje, použijte <xref:System.Net.CredentialCache> třídy za účelem vytvoření mezipaměti přihlašovací údaje místo zadávání je s každou žádostí.</span><span class="sxs-lookup"><span data-stu-id="cb29c-113">When accessing sites that require credentials, use the <xref:System.Net.CredentialCache> class to create a cache of credentials rather than supplying them with every request.</span></span> <span data-ttu-id="cb29c-114">**CredentialCache** třída vyhledá mezipaměti najít odpovídající přihlašovací údaje k dispozici s žádostí, můžete kerberosu zodpovědnosti při vytváření a prezentování přihlašovací údaje založené na adresu URL.</span><span class="sxs-lookup"><span data-stu-id="cb29c-114">The **CredentialCache** class searches the cache to find the appropriate credential to present with a request, relieving you of the responsibility of creating and presenting credentials based on the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb29c-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb29c-115">See Also</span></span>  
 [<span data-ttu-id="cb29c-116">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cb29c-116">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)
