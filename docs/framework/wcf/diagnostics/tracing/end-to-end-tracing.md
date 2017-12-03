---
title: "Komplexní trasování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5ac7fc7-f97c-4313-b068-54e0c471b2aa
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c3f5c9f80bbf124440952e35049969c7cfa4f19c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="end-to-end-tracing"></a><span data-ttu-id="db854-102">Komplexní trasování</span><span class="sxs-lookup"><span data-stu-id="db854-102">End-to-End Tracing</span></span>
<span data-ttu-id="db854-103">Koncová trasování (e2e) umožňuje vývojářům sledovat spuštění kódu v [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] infrastrukturu k prozkoumání, proč se nezdařilo kódové cestě nebo k poskytování podrobného trasování pro analýzu výkon a plánování kapacity.</span><span class="sxs-lookup"><span data-stu-id="db854-103">End to End (e2e) Tracing allows developers to follow the execution of code in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] infrastructure to investigate why a code path has failed, or to provide detailed tracing for capacity planning and performance analysis.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="db854-104">poskytuje tři korelace mechanismy pro usnadnění diagnostiky příčiny chybu: aktivit, přenosy a šíření.</span><span class="sxs-lookup"><span data-stu-id="db854-104"> provides three correlation mechanisms to help diagnose the cause of an error: activities, transfers, and propagation.</span></span>  
  
 <span data-ttu-id="db854-105">V tématu [scénáře trasování začátku do konce](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md) seznam trasování začátku do konce scénáře a jejich odpovídající aktivitu a trasování návrhu.</span><span class="sxs-lookup"><span data-stu-id="db854-105">See [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md) for a list of end-to-end tracing scenarios, and their respective activity and tracing design.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="db854-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="db854-106">In This Section</span></span>  
 <span data-ttu-id="db854-107">[Aktivita](../../../../../docs/framework/wcf/diagnostics/tracing/activity.md): popisuje aktivity trasování v [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] trasování modelu.</span><span class="sxs-lookup"><span data-stu-id="db854-107">[Activity](../../../../../docs/framework/wcf/diagnostics/tracing/activity.md):  Describes activity traces in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tracing model.</span></span>  
  
 <span data-ttu-id="db854-108">[Přenos](../../../../../docs/framework/wcf/diagnostics/tracing/transfer.md): popisuje přenos v [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] trasování modelu a pomocí přenosu ke korelaci aktivity v rámci koncové body.</span><span class="sxs-lookup"><span data-stu-id="db854-108">[Transfer](../../../../../docs/framework/wcf/diagnostics/tracing/transfer.md):  Describes transfer in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tracing model, and using transfer to correlate activities within endpoints.</span></span>  
  
 <span data-ttu-id="db854-109">[Šíření](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md): Popisuje rozšíření aktivity v [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] trasování modelu a pomocí šíření vazbu mezi aktivitami v koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="db854-109">[Propagation](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md):  Describes activity propagation in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tracing model, and using propagation to correlate activities across endpoints.</span></span>  
  
 [<span data-ttu-id="db854-110">Souhrn typů trasování</span><span class="sxs-lookup"><span data-stu-id="db854-110">Trace Type Summary</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/trace-type-summary.md)  
  
 <span data-ttu-id="db854-111">Poskytuje souhrn aktivity všech typů trasování</span><span class="sxs-lookup"><span data-stu-id="db854-111">Provides a summary of all activity trace types</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db854-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="db854-112">See Also</span></span>  
 [<span data-ttu-id="db854-113">Konfigurace trasování</span><span class="sxs-lookup"><span data-stu-id="db854-113">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [<span data-ttu-id="db854-114">Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení potíží</span><span class="sxs-lookup"><span data-stu-id="db854-114">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="db854-115">Scénáře začátku do konce trasování</span><span class="sxs-lookup"><span data-stu-id="db854-115">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [<span data-ttu-id="db854-116">Nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="db854-116">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
