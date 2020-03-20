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
ms.openlocfilehash: c7324dcbc27c95c7d799592700d46c195e7d952b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048897"
---
# <a name="best-practices-for-systemnet-classes"></a><span data-ttu-id="4daea-102">Osvědčené postupy pro třídy System.Net</span><span class="sxs-lookup"><span data-stu-id="4daea-102">Best Practices for System.Net Classes</span></span>
<span data-ttu-id="4daea-103">Následující doporučení vám pomohou použít třídy obsažené v <xref:System.Net> jejich nejlepší výhodě:</span><span class="sxs-lookup"><span data-stu-id="4daea-103">The following recommendations will help you use the classes contained in <xref:System.Net> to their best advantage:</span></span>  
  
- <span data-ttu-id="4daea-104">Doporučené postupy zabezpečení transportní vrstvy (TLS) naleznete v [doporučených postupech zabezpečení transportní vrstvy (TLS) pomocí rozhraní .NET Framework](tls.md).</span><span class="sxs-lookup"><span data-stu-id="4daea-104">For Transport Layer Security (TLS) best practices, see [Transport Layer Security (TLS) best practices with .NET Framework](tls.md).</span></span>

- <span data-ttu-id="4daea-105">Použití <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> a kdykoli je to možné místo typu odlévání do tříd potomků.</span><span class="sxs-lookup"><span data-stu-id="4daea-105">Use <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> whenever possible instead of type casting to descendant classes.</span></span> <span data-ttu-id="4daea-106">Aplikace, které používají **WebRequest** a **WebResponse** můžete využít nové internetové protokoly bez nutnosti rozsáhlé změny kódu.</span><span class="sxs-lookup"><span data-stu-id="4daea-106">Applications that use **WebRequest** and **WebResponse** can take advantage of new Internet protocols without needing extensive code changes.</span></span>  
  
- <span data-ttu-id="4daea-107">Při psaní ASP.NET aplikací, které běží na serveru pomocí **tříd System.Net,** je často lepší, z hlediska <xref:System.Net.WebRequest.GetResponse%2A> <xref:System.Net.WebResponse.GetResponseStream%2A>výkonu, používat asynchronní metody pro a .</span><span class="sxs-lookup"><span data-stu-id="4daea-107">When writing ASP.NET applications that run on a server using the **System.Net** classes, it is often better, from a performance standpoint, to use the asynchronous methods for <xref:System.Net.WebRequest.GetResponse%2A> and <xref:System.Net.WebResponse.GetResponseStream%2A>.</span></span>  
  
- <span data-ttu-id="4daea-108">Počet připojení otevřených k prostředku Sítě Internet může mít významný dopad na výkon sítě a propustnost.</span><span class="sxs-lookup"><span data-stu-id="4daea-108">The number of connections opened to an Internet resource can have a significant impact on network performance and throughput.</span></span> <span data-ttu-id="4daea-109">**System.Net** ve výchozím nastavení používá dvě připojení na aplikaci na hostitele.</span><span class="sxs-lookup"><span data-stu-id="4daea-109">**System.Net** uses two connections per application per host by default.</span></span> <span data-ttu-id="4daea-110">Nastavení <xref:System.Net.ServicePoint.ConnectionLimit%2A> vlastnosti <xref:System.Net.ServicePoint> pro vaši aplikaci může zvýšit toto číslo pro konkrétního hostitele.</span><span class="sxs-lookup"><span data-stu-id="4daea-110">Setting the <xref:System.Net.ServicePoint.ConnectionLimit%2A> property in the <xref:System.Net.ServicePoint> for your application can increase this number for a particular host.</span></span> <span data-ttu-id="4daea-111">Nastavení <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> vlastnosti může zvýšit toto výchozí nastavení pro všechny hostitele.</span><span class="sxs-lookup"><span data-stu-id="4daea-111">Setting the <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> property can increase this default for all hosts.</span></span>  
  
- <span data-ttu-id="4daea-112">Při psaní protokolů na úrovni <xref:System.Net.Sockets.TcpClient> soketu zkuste použít <xref:System.Net.Sockets.UdpClient> nebo <xref:System.Net.Sockets.Socket>kdykoli je to možné namísto zápisu přímo do .</span><span class="sxs-lookup"><span data-stu-id="4daea-112">When writing socket-level protocols, try to use <xref:System.Net.Sockets.TcpClient> or <xref:System.Net.Sockets.UdpClient> whenever possible instead of writing directly to a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="4daea-113">Tyto dvě třídy klienta zapouzdřují vytvoření soketů TCP a UDP bez nutnosti zpracování podrobností o připojení.</span><span class="sxs-lookup"><span data-stu-id="4daea-113">These two client classes encapsulate the creation of TCP and UDP sockets without requiring you to handle the details of the connection.</span></span>  
  
- <span data-ttu-id="4daea-114">Při přístupu k webům, <xref:System.Net.CredentialCache> které vyžadují pověření, použijte třídu k vytvoření mezipaměti pověření, nikoli k jejich poskytování s každým požadavkem.</span><span class="sxs-lookup"><span data-stu-id="4daea-114">When accessing sites that require credentials, use the <xref:System.Net.CredentialCache> class to create a cache of credentials rather than supplying them with every request.</span></span> <span data-ttu-id="4daea-115">Třída **CredentialCache** prohledá mezipaměť a vyhledá příslušné přihlašovací údaje, které bude prezentovat s požadavkem, a zmírní odpovědnost za vytváření a prezentaci přihlašovacích údajů na základě adresy URL.</span><span class="sxs-lookup"><span data-stu-id="4daea-115">The **CredentialCache** class searches the cache to find the appropriate credential to present with a request, relieving you of the responsibility of creating and presenting credentials based on the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4daea-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="4daea-116">See also</span></span>

- [<span data-ttu-id="4daea-117">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4daea-117">Network Programming in the .NET Framework</span></span>](index.md)
