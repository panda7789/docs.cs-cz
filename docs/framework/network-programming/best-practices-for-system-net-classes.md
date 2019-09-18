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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048897"
---
# <a name="best-practices-for-systemnet-classes"></a><span data-ttu-id="ca49a-102">Osvědčené postupy pro třídy System.Net</span><span class="sxs-lookup"><span data-stu-id="ca49a-102">Best Practices for System.Net Classes</span></span>
<span data-ttu-id="ca49a-103">Následující doporučení vám pomůžou používat třídy obsažené v aplikaci <xref:System.Net> k jejich nejlepší výhodě:</span><span class="sxs-lookup"><span data-stu-id="ca49a-103">The following recommendations will help you use the classes contained in <xref:System.Net> to their best advantage:</span></span>  
  
- <span data-ttu-id="ca49a-104">Doporučené postupy pro TLS (Transport Layer Security) najdete v tématu [osvědčené postupy TLS (Transport Layer Security) s .NET Framework](tls.md).</span><span class="sxs-lookup"><span data-stu-id="ca49a-104">For Transport Layer Security (TLS) best practices, see [Transport Layer Security (TLS) best practices with .NET Framework](tls.md).</span></span>

- <span data-ttu-id="ca49a-105">Používejte <xref:System.Net.WebRequest> a<xref:System.Net.WebResponse> kdykoli je to možné, namísto přetypování na odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="ca49a-105">Use <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> whenever possible instead of type casting to descendant classes.</span></span> <span data-ttu-id="ca49a-106">Aplikace, které používají **WebRequest** a **WebResponse** , můžou využívat nové internetové protokoly, aniž by museli provádět rozsáhlé změny kódu.</span><span class="sxs-lookup"><span data-stu-id="ca49a-106">Applications that use **WebRequest** and **WebResponse** can take advantage of new Internet protocols without needing extensive code changes.</span></span>  
  
- <span data-ttu-id="ca49a-107">Při psaní ASP.NET aplikací, které běží na serveru pomocí tříd **System.NET** , je často lepší, z hlediska výkonu, pro použití asynchronních metod pro <xref:System.Net.WebRequest.GetResponse%2A> a. <xref:System.Net.WebResponse.GetResponseStream%2A></span><span class="sxs-lookup"><span data-stu-id="ca49a-107">When writing ASP.NET applications that run on a server using the **System.Net** classes, it is often better, from a performance standpoint, to use the asynchronous methods for <xref:System.Net.WebRequest.GetResponse%2A> and <xref:System.Net.WebResponse.GetResponseStream%2A>.</span></span>  
  
- <span data-ttu-id="ca49a-108">Počet připojení otevřených k internetovému prostředku může mít významný dopad na výkon a propustnost sítě.</span><span class="sxs-lookup"><span data-stu-id="ca49a-108">The number of connections opened to an Internet resource can have a significant impact on network performance and throughput.</span></span> <span data-ttu-id="ca49a-109">**System.NET** používá ve výchozím nastavení dvě připojení na každou aplikaci na hostitele.</span><span class="sxs-lookup"><span data-stu-id="ca49a-109">**System.Net** uses two connections per application per host by default.</span></span> <span data-ttu-id="ca49a-110"><xref:System.Net.ServicePoint.ConnectionLimit%2A> Nastavení vlastnosti<xref:System.Net.ServicePoint> v pro aplikaci může zvýšit toto číslo pro konkrétního hostitele.</span><span class="sxs-lookup"><span data-stu-id="ca49a-110">Setting the <xref:System.Net.ServicePoint.ConnectionLimit%2A> property in the <xref:System.Net.ServicePoint> for your application can increase this number for a particular host.</span></span> <span data-ttu-id="ca49a-111"><xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> Nastavení vlastnosti může zvýšit tuto výchozí hodnotu pro všechny hostitele.</span><span class="sxs-lookup"><span data-stu-id="ca49a-111">Setting the <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> property can increase this default for all hosts.</span></span>  
  
- <span data-ttu-id="ca49a-112">Při psaní protokolů na úrovni soketu se pokuste použít <xref:System.Net.Sockets.TcpClient> nebo <xref:System.Net.Sockets.UdpClient> kdykoli je <xref:System.Net.Sockets.Socket>to možné, místo psaní přímo do.</span><span class="sxs-lookup"><span data-stu-id="ca49a-112">When writing socket-level protocols, try to use <xref:System.Net.Sockets.TcpClient> or <xref:System.Net.Sockets.UdpClient> whenever possible instead of writing directly to a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="ca49a-113">Tyto dvě klientské třídy zapouzdřují vytváření soketů TCP a UDP bez nutnosti zpracovávat podrobnosti o připojení.</span><span class="sxs-lookup"><span data-stu-id="ca49a-113">These two client classes encapsulate the creation of TCP and UDP sockets without requiring you to handle the details of the connection.</span></span>  
  
- <span data-ttu-id="ca49a-114">Při přístupu k lokalitám, které vyžadují přihlašovací <xref:System.Net.CredentialCache> údaje, použijte třídu k vytvoření mezipaměti přihlašovacích údajů místo jejich zadání se všemi požadavky.</span><span class="sxs-lookup"><span data-stu-id="ca49a-114">When accessing sites that require credentials, use the <xref:System.Net.CredentialCache> class to create a cache of credentials rather than supplying them with every request.</span></span> <span data-ttu-id="ca49a-115">Třída **CredentialCache** vyhledá v mezipaměti příslušné přihlašovací údaje, které mají být k dispozici s požadavkem, a tím vám zbavuje vytváření a prezentování přihlašovacích údajů na základě adresy URL.</span><span class="sxs-lookup"><span data-stu-id="ca49a-115">The **CredentialCache** class searches the cache to find the appropriate credential to present with a request, relieving you of the responsibility of creating and presenting credentials based on the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca49a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca49a-116">See also</span></span>

- [<span data-ttu-id="ca49a-117">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ca49a-117">Network Programming in the .NET Framework</span></span>](index.md)
