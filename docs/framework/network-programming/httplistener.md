---
title: HttpListener
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
ms.openlocfilehash: d5b07617617ac28e4f7f72bc23a96b45a85dff75
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047982"
---
# <a name="httplistener"></a><span data-ttu-id="608b0-102">HttpListener</span><span class="sxs-lookup"><span data-stu-id="608b0-102">HttpListener</span></span>
<span data-ttu-id="608b0-103"><xref:System.Net.HttpListener> Třída poskytuje programově řízený naslouchací proces protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="608b0-103">The <xref:System.Net.HttpListener> class provides a programmatically controlled HTTP protocol listener.</span></span> <span data-ttu-id="608b0-104">Naslouchací proces je aktivní po dobu života <xref:System.Net.HttpListener> objektu a běží v rámci aplikace.</span><span class="sxs-lookup"><span data-stu-id="608b0-104">The listener is active for the lifetime of the <xref:System.Net.HttpListener> object and runs within your application.</span></span>  
  
## <a name="httpsys"></a><span data-ttu-id="608b0-105">HTTP. TABULCE</span><span class="sxs-lookup"><span data-stu-id="608b0-105">HTTP.SYS</span></span>  
 <span data-ttu-id="608b0-106"><xref:System.Net.HttpListener> Třída je postavená na http. sys, což je naslouchací proces režimu jádra, který zpracovává veškerý provoz protokolu HTTP pro systém Windows.</span><span class="sxs-lookup"><span data-stu-id="608b0-106">The <xref:System.Net.HttpListener> class is built on top of HTTP.sys, which is the kernel mode listener that handles all HTTP traffic for Windows.</span></span> <span data-ttu-id="608b0-107">HTTP. sys poskytuje správu připojení, omezení šířky pásma a protokolování webového serveru.</span><span class="sxs-lookup"><span data-stu-id="608b0-107">HTTP.sys provides connection management, bandwidth throttling, and Web server logging.</span></span> <span data-ttu-id="608b0-108">Pomocí tohoto `HttpCfg.exe` nástroje přidejte certifikáty SSL.</span><span class="sxs-lookup"><span data-stu-id="608b0-108">Use the `HttpCfg.exe` tool to add SSL certificates.</span></span> <span data-ttu-id="608b0-109">Další informace najdete v dokumentaci k nástroji [Httpcfg. exe](https://go.microsoft.com/fwlink/?LinkID=178284) v dokumentaci k [serveru](https://go.microsoft.com/fwlink/?LinkID=178285) .</span><span class="sxs-lookup"><span data-stu-id="608b0-109">For more information, see the documentation on the [HttpCfg.exe](https://go.microsoft.com/fwlink/?LinkID=178284) tool in the [Server](https://go.microsoft.com/fwlink/?LinkID=178285) documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="608b0-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="608b0-110">See also</span></span>

- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpWebRequest>
- <xref:System.Net.HttpWebResponse>
- [<span data-ttu-id="608b0-111">HTTP Server</span><span class="sxs-lookup"><span data-stu-id="608b0-111">HTTP Server</span></span>](https://go.microsoft.com/fwlink/?LinkID=178285)
- [<span data-ttu-id="608b0-112">Vylepšení zabezpečení v internetové informační službě</span><span class="sxs-lookup"><span data-stu-id="608b0-112">Security Enhancements in Internet Information</span></span>](https://go.microsoft.com/fwlink/?LinkID=178286)
- [<span data-ttu-id="608b0-113">Ukázka hostitelské aplikace HttpListener ASPX</span><span class="sxs-lookup"><span data-stu-id="608b0-113">HttpListener ASPX Host Application Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179560)
- [<span data-ttu-id="608b0-114">Ukázka technologie HttpListener</span><span class="sxs-lookup"><span data-stu-id="608b0-114">HttpListener Technology Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179558)
- [<span data-ttu-id="608b0-115">Ukázky programování sítě</span><span class="sxs-lookup"><span data-stu-id="608b0-115">Network Programming Samples</span></span>](network-programming-samples.md)
