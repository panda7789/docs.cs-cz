---
title: Struktury pro hostování
ms.date: 03/30/2017
helpviewer_keywords:
- hosting structures [.NET Framework]
- unmanaged structures [.NET Framework], hosting
- structures [.NET Framework hosting]
ms.assetid: 492e010f-7493-4134-9505-f7008ccdaae6
ms.openlocfilehash: fb117352299a93aface6e58837307284ec4b8340
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616083"
---
# <a name="hosting-structures"></a><span data-ttu-id="ea45f-102">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="ea45f-102">Hosting Structures</span></span>
<span data-ttu-id="ea45f-103">Tato část popisuje nespravované struktury, které používá rozhraní API pro hostování.</span><span class="sxs-lookup"><span data-stu-id="ea45f-103">This section describes the unmanaged structures that the hosting API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ea45f-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ea45f-104">In This Section</span></span>  
 [<span data-ttu-id="ea45f-105">AssemblyBindInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="ea45f-105">AssemblyBindInfo Structure</span></span>](assemblybindinfo-structure.md)  
 <span data-ttu-id="ea45f-106">Poskytuje podrobné informace o odkazovaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="ea45f-106">Provides detailed information about the referenced assembly.</span></span>  
  
 [<span data-ttu-id="ea45f-107">BucketParameters – struktura</span><span class="sxs-lookup"><span data-stu-id="ea45f-107">BucketParameters Structure</span></span>](bucketparameters-structure.md)  
 <span data-ttu-id="ea45f-108">Ukládá název typu události a parametry pro aktuální výjimku, která je přidružena k události.</span><span class="sxs-lookup"><span data-stu-id="ea45f-108">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
 [<span data-ttu-id="ea45f-109">COR_GC_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="ea45f-109">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)  
 <span data-ttu-id="ea45f-110">Poskytuje statistiku o mechanizmu uvolňování paměti modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="ea45f-110">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
 [<span data-ttu-id="ea45f-111">COR_GC_THREAD_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="ea45f-111">COR_GC_THREAD_STATS Structure</span></span>](cor-gc-thread-stats-structure.md)  
 <span data-ttu-id="ea45f-112">Obsahuje statistiku jednotlivých vláken, která souvisí s uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="ea45f-112">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
 [<span data-ttu-id="ea45f-113">CustomDumpItem – struktura</span><span class="sxs-lookup"><span data-stu-id="ea45f-113">CustomDumpItem Structure</span></span>](customdumpitem-structure.md)  
 <span data-ttu-id="ea45f-114">Popisuje položku, která se má přidat do vlastního výpisu paměti při zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="ea45f-114">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
 [<span data-ttu-id="ea45f-115">MDAInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="ea45f-115">MDAInfo Structure</span></span>](mdainfo-structure.md)  
 <span data-ttu-id="ea45f-116">Poskytuje podrobnosti o `Event_MDAFired` události, které aktivují vytváření pomocníka spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="ea45f-116">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
 [<span data-ttu-id="ea45f-117">ModuleBindInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="ea45f-117">ModuleBindInfo Structure</span></span>](modulebindinfo-structure.md)  
 <span data-ttu-id="ea45f-118">Obsahuje podrobné informace o odkazovaném modulu a sestavení, které ho obsahuje.</span><span class="sxs-lookup"><span data-stu-id="ea45f-118">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
 [<span data-ttu-id="ea45f-119">StackOverflowInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="ea45f-119">StackOverflowInfo Structure</span></span>](stackoverflowinfo-structure.md)  
 <span data-ttu-id="ea45f-120">Ukládá typ přetečení, ke kterému došlo, a informace o výjimce, která byla vyvolána z důvodu přetečení.</span><span class="sxs-lookup"><span data-stu-id="ea45f-120">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ea45f-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ea45f-121">Related Sections</span></span>  
 [<span data-ttu-id="ea45f-122">Třídy typu coclass hostování</span><span class="sxs-lookup"><span data-stu-id="ea45f-122">Hosting Coclasses</span></span>](hosting-coclasses.md)  
  
 [<span data-ttu-id="ea45f-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="ea45f-123">Hosting Interfaces</span></span>](hosting-interfaces.md)  
  
 [<span data-ttu-id="ea45f-124">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="ea45f-124">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="ea45f-125">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="ea45f-125">Hosting Enumerations</span></span>](hosting-enumerations.md)
