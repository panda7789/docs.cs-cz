---
title: "Řešení potíží s aplikací pomocí trasování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7676b9bb-cbd1-41fd-9a93-cc615af6e2d0
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c04817d5a13c85f739f17fe25dd3c48ec9941a79
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-tracing-to-troubleshoot-your-application"></a><span data-ttu-id="fd2e5-102">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="fd2e5-102">Using Tracing to Troubleshoot Your Application</span></span>
<span data-ttu-id="fd2e5-103">Tato část obsahuje různé témata, které popisují, jak můžete použít trasování problém s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="fd2e5-103">This section contains various topics that describe how you can use tracing to troubleshoot your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fd2e5-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="fd2e5-104">In This Section</span></span>  
 [<span data-ttu-id="fd2e5-105">Doporučená nastavení pro trasování a protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="fd2e5-105">Recommended Settings for Tracing and Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)  
 <span data-ttu-id="fd2e5-106">Popisuje navrhované nastavení pro produkční a ladění prostředí.</span><span class="sxs-lookup"><span data-stu-id="fd2e5-106">Describes suggested settings for production and debugging environments.</span></span>  
  
 [<span data-ttu-id="fd2e5-107">Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení potíží</span><span class="sxs-lookup"><span data-stu-id="fd2e5-107">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 <span data-ttu-id="fd2e5-108">Popisuje, jak můžete použít nástroj prohlížeče trasování služeb k zobrazení, korelaci a analýze dat trasování.</span><span class="sxs-lookup"><span data-stu-id="fd2e5-108">Describes how you can use the Service Trace Viewer tool to view, correlate and analyze trace data.</span></span>  
  
 [<span data-ttu-id="fd2e5-109">Významná trasování</span><span class="sxs-lookup"><span data-stu-id="fd2e5-109">Significant Traces</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/significant-traces.md)  
 <span data-ttu-id="fd2e5-110">Seznam hlavních trasování vysílaných [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fd2e5-110">A list of major traces emitted by [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="fd2e5-111">Ladění na straně klienta</span><span class="sxs-lookup"><span data-stu-id="fd2e5-111">Debugging on the Client</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/debugging-on-the-client.md)  
 <span data-ttu-id="fd2e5-112">Umožňuje klientům ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="fd2e5-112">Enables clients to debug your application.</span></span>  
  
 [<span data-ttu-id="fd2e5-113">Scénáře začátku do konce trasování</span><span class="sxs-lookup"><span data-stu-id="fd2e5-113">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 <span data-ttu-id="fd2e5-114">Popisuje trasování použitý pro E2E [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] scénáře synchronní wsHttp odpovědi, například a asynchronní jednosměrný požadavky protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="fd2e5-114">Describes traces used for E2E [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] scenarios, for example, synchronous wsHttp request-replies, and asynchronous TCP one-way requests.</span></span>  
  
 [<span data-ttu-id="fd2e5-115">Generování trasování v uživatelském kódu</span><span class="sxs-lookup"><span data-stu-id="fd2e5-115">Emitting User-Code Traces</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md)  
 <span data-ttu-id="fd2e5-116">Popisuje, jak pro vydávání trasování prostřednictvím kódu programu v uživatelském kódu tak, aby proaktivně vytvořením data instrumentace pro pozdější použití pro účely diagnostiky a korelace s trasování WCF.</span><span class="sxs-lookup"><span data-stu-id="fd2e5-116">Describes how to emit traces programmatically in user code, so that you can proactively create instrumentation data to be used later for diagnostic purpose, and in correlation with WCF traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd2e5-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd2e5-117">See Also</span></span>  
 [<span data-ttu-id="fd2e5-118">Nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="fd2e5-118">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [<span data-ttu-id="fd2e5-119">Trasování</span><span class="sxs-lookup"><span data-stu-id="fd2e5-119">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="fd2e5-120">Konec Konec trasování</span><span class="sxs-lookup"><span data-stu-id="fd2e5-120">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
