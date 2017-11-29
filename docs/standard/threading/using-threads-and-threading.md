---
title: "Použití vláken a dělení na vlákna"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 80eb4c3bb98acdd1f83dbf5bcf57b2f7b295742b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="using-threads-and-threading"></a><span data-ttu-id="2d5d3-102">Použití vláken a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="2d5d3-102">Using Threads and Threading</span></span>
<span data-ttu-id="2d5d3-103">Témata v této části popisují vytváření a správu spravovaných vláknech, jak předat data do spravovaných vláknech a získat výsledky zpět a zrušení vláken a zpracování <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="2d5d3-103">The topics in this section discuss the creation and management of managed threads, how to pass data to managed threads and get results back, and how to destroy threads and handle a <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2d5d3-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2d5d3-104">In This Section</span></span>  
 [<span data-ttu-id="2d5d3-105">Vytváření vláken a předávání dat při spuštění</span><span class="sxs-lookup"><span data-stu-id="2d5d3-105">Creating Threads and Passing Data at Start Time</span></span>](../../../docs/standard/threading/creating-threads-and-passing-data-at-start-time.md)  
 <span data-ttu-id="2d5d3-106">Popisuje a předvádí vytvoření spravovaných vláknech, včetně jak předat data do nové vláken a jak data nelze vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="2d5d3-106">Discusses and demonstrates the creation of managed threads, including how to pass data to new threads and how to get data back.</span></span>  
  
 [<span data-ttu-id="2d5d3-107">Pozastavování a obnovování vláken</span><span class="sxs-lookup"><span data-stu-id="2d5d3-107">Pausing and Resuming Threads</span></span>](../../../docs/standard/threading/pausing-and-resuming-threads.md)  
 <span data-ttu-id="2d5d3-108">Popisuje následky pozastavení a obnovení spravovaných vláken.</span><span class="sxs-lookup"><span data-stu-id="2d5d3-108">Discusses the ramifications of pausing and resuming managed threads.</span></span>  
  
 [<span data-ttu-id="2d5d3-109">Zničení vláken</span><span class="sxs-lookup"><span data-stu-id="2d5d3-109">Destroying Threads</span></span>](../../../docs/standard/threading/destroying-threads.md)  
 <span data-ttu-id="2d5d3-110">Popisuje strukturu zničení spravovaných vláknech a jak bude zpracováván <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="2d5d3-110">Discusses the ramifications of destroying managed threads, and how to handle a <xref:System.Threading.ThreadAbortException>.</span></span>  
  
 [<span data-ttu-id="2d5d3-111">Plánování vláken</span><span class="sxs-lookup"><span data-stu-id="2d5d3-111">Scheduling Threads</span></span>](../../../docs/standard/threading/scheduling-threads.md)  
 <span data-ttu-id="2d5d3-112">Popisuje priority přístup z více vláken a jejich vliv na plánování přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="2d5d3-112">Discusses thread priorities and how they affect thread scheduling.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2d5d3-113">Odkaz</span><span class="sxs-lookup"><span data-stu-id="2d5d3-113">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="2d5d3-114">Poskytuje referenční dokumentaci pro <xref:System.Threading.Thread> třídy, která představuje spravované vlákno, v tom, zda pochází nespravovaného kódu nebo byl vytvořen ve spravované aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2d5d3-114">Provides reference documentation for the <xref:System.Threading.Thread> class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.Threading.ThreadStart>  
 <span data-ttu-id="2d5d3-115">Poskytuje referenční dokumentaci pro <xref:System.Threading.ThreadStart> delegáta, který představuje postupy vlákno bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="2d5d3-115">Provides reference documentation for the <xref:System.Threading.ThreadStart> delegate that represents parameterless thread procedures.</span></span>  
  
 <xref:System.Threading.ParameterizedThreadStart>  
 <span data-ttu-id="2d5d3-116">Poskytuje snadný způsob, jak předat data do postup přístup z více vláken, i když bez silného typování.</span><span class="sxs-lookup"><span data-stu-id="2d5d3-116">Provides an easy way to pass data to a thread procedure, although without strong typing.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2d5d3-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="2d5d3-117">Related Sections</span></span>  
 [<span data-ttu-id="2d5d3-118">Vlákna a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="2d5d3-118">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="2d5d3-119">Poskytuje úvod do spravovaného dělení na vlákna.</span><span class="sxs-lookup"><span data-stu-id="2d5d3-119">Provides an introduction to managed threading.</span></span>
