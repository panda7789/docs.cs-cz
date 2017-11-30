---
title: "Události Trasování událostí pro Windows v CLR (Common Language Runtime)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a8313a6b06387f6fd0a5f95191ea57bdf034c372
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2017
---
# <a name="etw-events-in-the-common-language-runtime"></a><span data-ttu-id="2abd6-102">Události Trasování událostí pro Windows v CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="2abd6-102">ETW Events in the Common Language Runtime</span></span>
<span data-ttu-id="2abd6-103">Modul CLR (CLR) poskytuje trasování užitečné událostí pro Windows (ETW) diagnostické informace prostřednictvím širokou škálu ladění a profilování události.</span><span class="sxs-lookup"><span data-stu-id="2abd6-103">The common language runtime (CLR) provides useful event tracing for Windows (ETW) diagnostic information through a large variety of debugging and profiling events.</span></span> <span data-ttu-id="2abd6-104">CLR ETW – události využít systému trasování Windows ETW k posílení existující profilace a ladění podpora poskytované modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="2abd6-104">CLR ETW events leverage the Windows ETW tracing system to augment the existing profiling and debugging support provided by the common language runtime.</span></span>  
  
 <span data-ttu-id="2abd6-105">Další informace o trasování událostí pro Windows najdete v článku [vylepšení ladění a optimalizace výkonu s ETW](http://go.microsoft.com/fwlink/?LinkID=161142) na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="2abd6-105">More information about ETW is available in the article [Improve Debugging and Performance Tuning with ETW](http://go.microsoft.com/fwlink/?LinkID=161142) on MSDN.</span></span> <span data-ttu-id="2abd6-106">Informace o Xperf lze najít v položce [nástrojů výkonu systému Windows - Xperf](http://go.microsoft.com/fwlink/?LinkID=161144) v blogu NTDebugging.</span><span class="sxs-lookup"><span data-stu-id="2abd6-106">Information about Xperf can be found in the entry [Windows Performance Toolkit - Xperf](http://go.microsoft.com/fwlink/?LinkID=161144) in the NTDebugging blog.</span></span>  
  
 <span data-ttu-id="2abd6-107">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] Nebo novější je vyžadován pro všechny události popsané události témata.</span><span class="sxs-lookup"><span data-stu-id="2abd6-107">The [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] or later is required for all the events described in the event topics.</span></span> <span data-ttu-id="2abd6-108">Je minimální podporované klientské operační systém Windows Vista a Windows Server 2008 je serverem minimální podporované.</span><span class="sxs-lookup"><span data-stu-id="2abd6-108">The Windows Vista operating system is the minimum supported client, and Windows Server 2008 is the minimum supported server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2abd6-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2abd6-109">In This Section</span></span>  
 [<span data-ttu-id="2abd6-110">Řízení přihlašování rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2abd6-110">Controlling .NET Framework Logging</span></span>](../../../docs/framework/performance/controlling-logging.md)  
 <span data-ttu-id="2abd6-111">Popisuje nástroje a příkazy pro zaznamenání a zobrazování událostí trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="2abd6-111">Describes the tools and commands for capturing and viewing ETW events.</span></span>  
  
 [<span data-ttu-id="2abd6-112">CLR ETW – zprostředkovatelé</span><span class="sxs-lookup"><span data-stu-id="2abd6-112">CLR ETW Providers</span></span>](../../../docs/framework/performance/clr-etw-providers.md)  
 <span data-ttu-id="2abd6-113">Poskytuje informace o modulu runtime a sekvence daneho poskytovatelů a jak je můžete použít pro shromažďování dat trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="2abd6-113">Provides information about the runtime and rundown providers, and how you can use them for ETW data collection.</span></span>  
  
 [<span data-ttu-id="2abd6-114">CLR ETW – klíčová slova a úrovně</span><span class="sxs-lookup"><span data-stu-id="2abd6-114">CLR ETW Keywords and Levels</span></span>](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)  
 <span data-ttu-id="2abd6-115">Popisuje klíčová slova pro modul Runtime a sekvence daneho poskytovatelů, které umožňují filtrování událostí podle kategorie.</span><span class="sxs-lookup"><span data-stu-id="2abd6-115">Describes the keywords for the Runtime and Rundown providers that enable the filtering of events by category.</span></span>  
  
 [<span data-ttu-id="2abd6-116">CLR ETW – události</span><span class="sxs-lookup"><span data-stu-id="2abd6-116">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)  
 <span data-ttu-id="2abd6-117">Poskytuje podrobné informace o CLR ETW události, klíčová slova, úrovně a data události.</span><span class="sxs-lookup"><span data-stu-id="2abd6-117">Provides detailed information about CLR ETW events, their keywords, levels, and event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2abd6-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="2abd6-118">See Also</span></span>  
 [<span data-ttu-id="2abd6-119">Události trasování událostí pro Windows v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2abd6-119">ETW Events in the .NET Framework</span></span>](../../../docs/framework/performance/etw-events.md)
