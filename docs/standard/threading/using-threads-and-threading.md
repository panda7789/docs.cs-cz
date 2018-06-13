---
title: Použití vláken a dělení na vlákna
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 725a47cae6e3e91cf9e7385427bceece81f3c918
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584177"
---
# <a name="using-threads-and-threading"></a><span data-ttu-id="f965b-102">Použití vláken a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="f965b-102">Using Threads and Threading</span></span>
<span data-ttu-id="f965b-103">Témata v této části popisují vytváření a správu spravovaných vláknech, jak předat data do spravovaných vláknech a získat výsledky zpět a zrušení vláken a zpracování <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="f965b-103">The topics in this section discuss the creation and management of managed threads, how to pass data to managed threads and get results back, and how to destroy threads and handle a <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f965b-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f965b-104">In This Section</span></span>  
 [<span data-ttu-id="f965b-105">Vytváření vláken a předávání dat při spuštění</span><span class="sxs-lookup"><span data-stu-id="f965b-105">Creating Threads and Passing Data at Start Time</span></span>](../../../docs/standard/threading/creating-threads-and-passing-data-at-start-time.md)  
 <span data-ttu-id="f965b-106">Popisuje a předvádí vytvoření spravovaných vláknech, včetně jak předat data do nové vláken a jak data nelze vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="f965b-106">Discusses and demonstrates the creation of managed threads, including how to pass data to new threads and how to get data back.</span></span>  
  
 [<span data-ttu-id="f965b-107">Pozastavování a obnovování vláken</span><span class="sxs-lookup"><span data-stu-id="f965b-107">Pausing and Resuming Threads</span></span>](../../../docs/standard/threading/pausing-and-resuming-threads.md)  
 <span data-ttu-id="f965b-108">Popisuje následky pozastavení a obnovení spravovaných vláken.</span><span class="sxs-lookup"><span data-stu-id="f965b-108">Discusses the ramifications of pausing and resuming managed threads.</span></span>  
  
 [<span data-ttu-id="f965b-109">Zničení vláken</span><span class="sxs-lookup"><span data-stu-id="f965b-109">Destroying Threads</span></span>](../../../docs/standard/threading/destroying-threads.md)  
 <span data-ttu-id="f965b-110">Popisuje strukturu zničení spravovaných vláknech a jak bude zpracováván <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="f965b-110">Discusses the ramifications of destroying managed threads, and how to handle a <xref:System.Threading.ThreadAbortException>.</span></span>  
  
 [<span data-ttu-id="f965b-111">Plánování vláken</span><span class="sxs-lookup"><span data-stu-id="f965b-111">Scheduling Threads</span></span>](../../../docs/standard/threading/scheduling-threads.md)  
 <span data-ttu-id="f965b-112">Popisuje priority přístup z více vláken a jejich vliv na plánování přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="f965b-112">Discusses thread priorities and how they affect thread scheduling.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f965b-113">Odkaz</span><span class="sxs-lookup"><span data-stu-id="f965b-113">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="f965b-114">Poskytuje referenční dokumentaci pro <xref:System.Threading.Thread> třídy, která představuje spravované vlákno, v tom, zda pochází nespravovaného kódu nebo byl vytvořen ve spravované aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f965b-114">Provides reference documentation for the <xref:System.Threading.Thread> class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.Threading.ThreadStart>  
 <span data-ttu-id="f965b-115">Poskytuje referenční dokumentaci pro <xref:System.Threading.ThreadStart> delegáta, který představuje postupy vlákno bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="f965b-115">Provides reference documentation for the <xref:System.Threading.ThreadStart> delegate that represents parameterless thread procedures.</span></span>  
  
 <xref:System.Threading.ParameterizedThreadStart>  
 <span data-ttu-id="f965b-116">Poskytuje snadný způsob, jak předat data do postup přístup z více vláken, i když bez silného typování.</span><span class="sxs-lookup"><span data-stu-id="f965b-116">Provides an easy way to pass data to a thread procedure, although without strong typing.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f965b-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="f965b-117">Related Sections</span></span>  
 [<span data-ttu-id="f965b-118">Vlákna a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="f965b-118">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="f965b-119">Poskytuje úvod do spravovaného dělení na vlákna.</span><span class="sxs-lookup"><span data-stu-id="f965b-119">Provides an introduction to managed threading.</span></span>
