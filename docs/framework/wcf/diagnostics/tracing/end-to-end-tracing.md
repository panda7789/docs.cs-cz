---
title: Komplexní trasování
ms.date: 03/30/2017
ms.assetid: f5ac7fc7-f97c-4313-b068-54e0c471b2aa
ms.openlocfilehash: fc8fc448bdcf94ab25349f6b34961a34e5ed2a5a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598577"
---
# <a name="end-to-end-tracing"></a><span data-ttu-id="1378f-102">Komplexní trasování</span><span class="sxs-lookup"><span data-stu-id="1378f-102">End-to-End Tracing</span></span>
<span data-ttu-id="1378f-103">Koncové trasování (e2e) umožňuje vývojářům sledovat spuštění kódu v infrastruktuře Windows Communication Foundation (WCF) a prozkoumat, proč se cesta k kódu nezdařila, nebo poskytnout podrobné trasování pro plánování kapacity a analýzu výkonu.</span><span class="sxs-lookup"><span data-stu-id="1378f-103">End to End (e2e) Tracing allows developers to follow the execution of code in the Windows Communication Foundation (WCF) infrastructure to investigate why a code path has failed, or to provide detailed tracing for capacity planning and performance analysis.</span></span> <span data-ttu-id="1378f-104">Windows Communication Foundation (WCF) poskytuje tři mechanismy korelace, které vám pomůžou diagnostikovat příčinu chyby: aktivity, přenosy a šíření.</span><span class="sxs-lookup"><span data-stu-id="1378f-104">Windows Communication Foundation (WCF) provides three correlation mechanisms to help diagnose the cause of an error: activities, transfers, and propagation.</span></span>  
  
 <span data-ttu-id="1378f-105">V tématu [ucelené scénáře trasování](end-to-end-tracing-scenarios.md) najdete seznam kompletních scénářů trasování a jejich činnost a návrh trasování.</span><span class="sxs-lookup"><span data-stu-id="1378f-105">See [End-To-End Tracing Scenarios](end-to-end-tracing-scenarios.md) for a list of end-to-end tracing scenarios, and their respective activity and tracing design.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1378f-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1378f-106">In This Section</span></span>  
 <span data-ttu-id="1378f-107">[Activity](activity.md): popisuje trasování aktivit v modelu trasování Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1378f-107">[Activity](activity.md):  Describes activity traces in the Windows Communication Foundation (WCF) tracing model.</span></span>  
  
 <span data-ttu-id="1378f-108">[Transfer](transfer.md): popisuje přenos v modelu trasování Windows Communication Foundation (WCF) a použití přenosu ke korelaci aktivit v rámci koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="1378f-108">[Transfer](transfer.md):  Describes transfer in the Windows Communication Foundation (WCF) tracing model, and using transfer to correlate activities within endpoints.</span></span>  
  
 <span data-ttu-id="1378f-109">[Šíření](propagation.md): popisuje šíření aktivity v modelu trasování Windows Communication Foundation (WCF) a použití šíření ke korelaci aktivit mezi koncovými body.</span><span class="sxs-lookup"><span data-stu-id="1378f-109">[Propagation](propagation.md):  Describes activity propagation in the Windows Communication Foundation (WCF) tracing model, and using propagation to correlate activities across endpoints.</span></span>  
  
 [<span data-ttu-id="1378f-110">Souhrn typů trasování</span><span class="sxs-lookup"><span data-stu-id="1378f-110">Trace Type Summary</span></span>](trace-type-summary.md)  
  
 <span data-ttu-id="1378f-111">Poskytuje souhrn všech typů trasování aktivit.</span><span class="sxs-lookup"><span data-stu-id="1378f-111">Provides a summary of all activity trace types</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1378f-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="1378f-112">See also</span></span>

- [<span data-ttu-id="1378f-113">Konfigurace trasování</span><span class="sxs-lookup"><span data-stu-id="1378f-113">Configuring Tracing</span></span>](configuring-tracing.md)
- [<span data-ttu-id="1378f-114">Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů</span><span class="sxs-lookup"><span data-stu-id="1378f-114">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="1378f-115">Scénáře komplexního trasování</span><span class="sxs-lookup"><span data-stu-id="1378f-115">End-To-End Tracing Scenarios</span></span>](end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="1378f-116">Prohlížeč trasování služeb (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="1378f-116">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
