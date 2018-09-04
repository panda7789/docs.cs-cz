---
title: HttpListener
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 68c69de839ccbd51de9f0bfa74be018f877f7731
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43555585"
---
# <a name="httplistener"></a><span data-ttu-id="91f2b-102">HttpListener</span><span class="sxs-lookup"><span data-stu-id="91f2b-102">HttpListener</span></span>
<span data-ttu-id="91f2b-103"><xref:System.Net.HttpListener> Třída poskytuje programově řízené naslouchací proces protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="91f2b-103">The <xref:System.Net.HttpListener> class provides a programmatically controlled HTTP protocol listener.</span></span> <span data-ttu-id="91f2b-104">Naslouchací proces je aktivní po dobu životnosti <xref:System.Net.HttpListener> objektu a běží v rámci vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="91f2b-104">The listener is active for the lifetime of the <xref:System.Net.HttpListener> object and runs within your application.</span></span>  
  
## <a name="httpsys"></a><span data-ttu-id="91f2b-105">HTTP. SYS</span><span class="sxs-lookup"><span data-stu-id="91f2b-105">HTTP.SYS</span></span>  
 <span data-ttu-id="91f2b-106"><xref:System.Net.HttpListener> Třídy je založená na základě ovladače HTTP.sys, což je režim jádra naslouchací proces, který zpracovává všechen provoz protokolu HTTP pro Windows.</span><span class="sxs-lookup"><span data-stu-id="91f2b-106">The <xref:System.Net.HttpListener> class is built on top of HTTP.sys, which is the kernel mode listener that handles all HTTP traffic for Windows.</span></span> <span data-ttu-id="91f2b-107">Ovladač HTTP.sys poskytuje správu připojení, omezení šířky pásma a protokolování webového serveru.</span><span class="sxs-lookup"><span data-stu-id="91f2b-107">HTTP.sys provides connection management, bandwidth throttling, and Web server logging.</span></span> <span data-ttu-id="91f2b-108">Použití `HttpCfg.exe` nástroj přidat certifikáty SSL.</span><span class="sxs-lookup"><span data-stu-id="91f2b-108">Use the `HttpCfg.exe` tool to add SSL certificates.</span></span> <span data-ttu-id="91f2b-109">Další informace najdete v dokumentaci na [HttpCfg.exe](https://go.microsoft.com/fwlink/?LinkID=178284) nástroj v [Server](https://go.microsoft.com/fwlink/?LinkID=178285) dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="91f2b-109">For more information, see the documentation on the [HttpCfg.exe](https://go.microsoft.com/fwlink/?LinkID=178284) tool in the [Server](https://go.microsoft.com/fwlink/?LinkID=178285) documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91f2b-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="91f2b-110">See Also</span></span>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.HttpWebResponse>  
 [<span data-ttu-id="91f2b-111">HTTP Server</span><span class="sxs-lookup"><span data-stu-id="91f2b-111">HTTP Server</span></span>](https://go.microsoft.com/fwlink/?LinkID=178285)  
 [<span data-ttu-id="91f2b-112">Vylepšení zabezpečení v Internetové informační</span><span class="sxs-lookup"><span data-stu-id="91f2b-112">Security Enhancements in Internet Information</span></span>](https://go.microsoft.com/fwlink/?LinkID=178286)  
 [<span data-ttu-id="91f2b-113">Ukázkové aplikace hostitele HttpListener ASPX</span><span class="sxs-lookup"><span data-stu-id="91f2b-113">HttpListener ASPX Host Application Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179560)  
 [<span data-ttu-id="91f2b-114">Ukázka technologie HttpListener</span><span class="sxs-lookup"><span data-stu-id="91f2b-114">HttpListener Technology Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179558)  
 [<span data-ttu-id="91f2b-115">Ukázky programování sítě</span><span class="sxs-lookup"><span data-stu-id="91f2b-115">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)
