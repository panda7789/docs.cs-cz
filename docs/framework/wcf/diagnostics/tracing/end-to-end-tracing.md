---
title: Komplexní trasování
ms.date: 03/30/2017
ms.assetid: f5ac7fc7-f97c-4313-b068-54e0c471b2aa
ms.openlocfilehash: fd2964b39c758e41620fb453ddd8f61a1aa550aa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092112"
---
# <a name="end-to-end-tracing"></a><span data-ttu-id="75abd-102">Komplexní trasování</span><span class="sxs-lookup"><span data-stu-id="75abd-102">End-to-End Tracing</span></span>
<span data-ttu-id="75abd-103">Kompletní (e2e) trasování umožňuje vývojářům sledovat spuštění kódu v prozkoumat, proč se nezdařilo kódové cestě, nebo poskytnout podrobné trasování pro analýzu výkon a plánování kapacity pro infrastrukturu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="75abd-103">End to End (e2e) Tracing allows developers to follow the execution of code in the Windows Communication Foundation (WCF) infrastructure to investigate why a code path has failed, or to provide detailed tracing for capacity planning and performance analysis.</span></span> <span data-ttu-id="75abd-104">Windows Communication Foundation (WCF) poskytuje tři mechanismy korelace pro usnadnění diagnostiky příčiny chyby: aktivit, přenosy a šíření.</span><span class="sxs-lookup"><span data-stu-id="75abd-104">Windows Communication Foundation (WCF) provides three correlation mechanisms to help diagnose the cause of an error: activities, transfers, and propagation.</span></span>  
  
 <span data-ttu-id="75abd-105">Zobrazit [scénáře trasování začátku do konce](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md) seznam scénáře trasování začátku do konce a jejich odpovídajících aktivit a trasování návrhu.</span><span class="sxs-lookup"><span data-stu-id="75abd-105">See [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md) for a list of end-to-end tracing scenarios, and their respective activity and tracing design.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="75abd-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="75abd-106">In This Section</span></span>  
 <span data-ttu-id="75abd-107">[Aktivita](../../../../../docs/framework/wcf/diagnostics/tracing/activity.md):  Popisuje aktivity trasování v modelu trasování Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="75abd-107">[Activity](../../../../../docs/framework/wcf/diagnostics/tracing/activity.md):  Describes activity traces in the Windows Communication Foundation (WCF) tracing model.</span></span>  
  
 <span data-ttu-id="75abd-108">[Přenos](../../../../../docs/framework/wcf/diagnostics/tracing/transfer.md):  Popisuje přenosu v modelu trasování Windows Communication Foundation (WCF) a pomocí přenosu v korelovat aktivity v rámci koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="75abd-108">[Transfer](../../../../../docs/framework/wcf/diagnostics/tracing/transfer.md):  Describes transfer in the Windows Communication Foundation (WCF) tracing model, and using transfer to correlate activities within endpoints.</span></span>  
  
 <span data-ttu-id="75abd-109">[Šíření](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md):  Popisuje rozšíření aktivity v Windows Communication Foundation (WCF) trasování modelu a pomocí šíření korelovat aktivity napříč koncovými body.</span><span class="sxs-lookup"><span data-stu-id="75abd-109">[Propagation](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md):  Describes activity propagation in the Windows Communication Foundation (WCF) tracing model, and using propagation to correlate activities across endpoints.</span></span>  
  
 [<span data-ttu-id="75abd-110">Souhrn typů trasování</span><span class="sxs-lookup"><span data-stu-id="75abd-110">Trace Type Summary</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/trace-type-summary.md)  
  
 <span data-ttu-id="75abd-111">Poskytuje přehled všech aktivit typů trasování</span><span class="sxs-lookup"><span data-stu-id="75abd-111">Provides a summary of all activity trace types</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75abd-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75abd-112">See also</span></span>

- [<span data-ttu-id="75abd-113">Konfigurace trasování</span><span class="sxs-lookup"><span data-stu-id="75abd-113">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [<span data-ttu-id="75abd-114">Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů</span><span class="sxs-lookup"><span data-stu-id="75abd-114">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="75abd-115">Scénáře komplexního trasování</span><span class="sxs-lookup"><span data-stu-id="75abd-115">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="75abd-116">Prohlížeč trasování služeb (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="75abd-116">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
