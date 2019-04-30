---
title: Osvědčené postupy pro třídy System.Net
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
ms.openlocfilehash: 5bb3ac545613da68d5f370fefbf94b674b70fe64
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61866805"
---
# <a name="best-practices-for-systemnet-classes"></a><span data-ttu-id="122dc-102">Osvědčené postupy pro třídy System.Net</span><span class="sxs-lookup"><span data-stu-id="122dc-102">Best Practices for System.Net Classes</span></span>
<span data-ttu-id="122dc-103">Následující doporučení vám pomůže s použitím třídy obsažené v <xref:System.Net> k jejich přinášelo maximální výhody:</span><span class="sxs-lookup"><span data-stu-id="122dc-103">The following recommendations will help you use the classes contained in <xref:System.Net> to their best advantage:</span></span>  
  
- <span data-ttu-id="122dc-104">Osvědčené postupy zabezpečení TLS (Transport Layer), najdete v části [zabezpečení TLS (Transport Layer) osvědčené postupy s rozhraním .NET Framework](tls.md).</span><span class="sxs-lookup"><span data-stu-id="122dc-104">For Transport Layer Security (TLS) best practices, see [Transport Layer Security (TLS) best practices with .NET Framework](tls.md).</span></span>

- <span data-ttu-id="122dc-105">Použití <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> kdykoli je to možné, ne přetypování typu na odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="122dc-105">Use <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> whenever possible instead of type casting to descendant classes.</span></span> <span data-ttu-id="122dc-106">Aplikace, které používají **WebRequest** a **WebResponse** můžete využívat nové internetové protokoly bez nutnosti rozsáhlého kódu změny.</span><span class="sxs-lookup"><span data-stu-id="122dc-106">Applications that use **WebRequest** and **WebResponse** can take advantage of new Internet protocols without needing extensive code changes.</span></span>  
  
- <span data-ttu-id="122dc-107">Při psaní aplikací ASP.NET, které běží na serveru pomocí **System.Net** třídy, je často vhodnější, z hlediska výkonu použít asynchronní metody pro <xref:System.Net.WebRequest.GetResponse%2A> a <xref:System.Net.WebResponse.GetResponseStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="122dc-107">When writing ASP.NET applications that run on a server using the **System.Net** classes, it is often better, from a performance standpoint, to use the asynchronous methods for <xref:System.Net.WebRequest.GetResponse%2A> and <xref:System.Net.WebResponse.GetResponseStream%2A>.</span></span>  
  
- <span data-ttu-id="122dc-108">Počet otevřených připojení k internetového zdroji může mít významný dopad na výkon sítě a propustnost.</span><span class="sxs-lookup"><span data-stu-id="122dc-108">The number of connections opened to an Internet resource can have a significant impact on network performance and throughput.</span></span> <span data-ttu-id="122dc-109">**System.Net** ve výchozím nastavení používá dvě spojení na aplikaci na hostitele.</span><span class="sxs-lookup"><span data-stu-id="122dc-109">**System.Net** uses two connections per application per host by default.</span></span> <span data-ttu-id="122dc-110">Nastavení <xref:System.Net.ServicePoint.ConnectionLimit%2A> vlastnost <xref:System.Net.ServicePoint> pro vaše aplikace toto číslo můžete navýšit pro konkrétního hostitele.</span><span class="sxs-lookup"><span data-stu-id="122dc-110">Setting the <xref:System.Net.ServicePoint.ConnectionLimit%2A> property in the <xref:System.Net.ServicePoint> for your application can increase this number for a particular host.</span></span> <span data-ttu-id="122dc-111">Nastavení <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> vlastnost zvýšit toto výchozí nastavení pro všechny hostitele.</span><span class="sxs-lookup"><span data-stu-id="122dc-111">Setting the <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> property can increase this default for all hosts.</span></span>  
  
- <span data-ttu-id="122dc-112">Při zápisu protokoly na úrovni soketu, zkuste použít <xref:System.Net.Sockets.TcpClient> nebo <xref:System.Net.Sockets.UdpClient> kdykoli je to možné místo psaní přímo <xref:System.Net.Sockets.Socket>.</span><span class="sxs-lookup"><span data-stu-id="122dc-112">When writing socket-level protocols, try to use <xref:System.Net.Sockets.TcpClient> or <xref:System.Net.Sockets.UdpClient> whenever possible instead of writing directly to a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="122dc-113">Tyto dva klientské zapouzdřují vytváření TCP a UDP sockets aniž by bylo potřeba zpracovat podrobné údaje o připojení.</span><span class="sxs-lookup"><span data-stu-id="122dc-113">These two client classes encapsulate the creation of TCP and UDP sockets without requiring you to handle the details of the connection.</span></span>  
  
- <span data-ttu-id="122dc-114">Pokud přístup k serverům, které vyžadují přihlašovací údaje, použijte <xref:System.Net.CredentialCache> třídy za účelem vytvoření mezipaměti přihlašovacích údajů namísto zadávání při každé žádosti.</span><span class="sxs-lookup"><span data-stu-id="122dc-114">When accessing sites that require credentials, use the <xref:System.Net.CredentialCache> class to create a cache of credentials rather than supplying them with every request.</span></span> <span data-ttu-id="122dc-115">**CredentialCache** třídy vyhledá mezipaměti k vyhledání příslušné přihlašovací údaje prezentovat s žádostí, můžete homogenního odpovědnosti, vytváření a prezentování přihlašovací údaje podle zadané adresy URL.</span><span class="sxs-lookup"><span data-stu-id="122dc-115">The **CredentialCache** class searches the cache to find the appropriate credential to present with a request, relieving you of the responsibility of creating and presenting credentials based on the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="122dc-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="122dc-116">See also</span></span>

- [<span data-ttu-id="122dc-117">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="122dc-117">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)
