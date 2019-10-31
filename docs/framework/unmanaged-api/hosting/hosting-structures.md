---
title: Struktury pro hostování
ms.date: 03/30/2017
helpviewer_keywords:
- hosting structures [.NET Framework]
- unmanaged structures [.NET Framework], hosting
- structures [.NET Framework hosting]
ms.assetid: 492e010f-7493-4134-9505-f7008ccdaae6
ms.openlocfilehash: 3d43225574b8794733ee2e83562699276ddc5bab
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126941"
---
# <a name="hosting-structures"></a><span data-ttu-id="815d0-102">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="815d0-102">Hosting Structures</span></span>
<span data-ttu-id="815d0-103">Tato část popisuje nespravované struktury, které používá rozhraní API pro hostování.</span><span class="sxs-lookup"><span data-stu-id="815d0-103">This section describes the unmanaged structures that the hosting API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="815d0-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="815d0-104">In This Section</span></span>  
 [<span data-ttu-id="815d0-105">AssemblyBindInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="815d0-105">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)  
 <span data-ttu-id="815d0-106">Poskytuje podrobné informace o odkazovaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="815d0-106">Provides detailed information about the referenced assembly.</span></span>  
  
 [<span data-ttu-id="815d0-107">BucketParameters – struktura</span><span class="sxs-lookup"><span data-stu-id="815d0-107">BucketParameters Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md)  
 <span data-ttu-id="815d0-108">Ukládá název typu události a parametry pro aktuální výjimku, která je přidružena k události.</span><span class="sxs-lookup"><span data-stu-id="815d0-108">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
 [<span data-ttu-id="815d0-109">COR_GC_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="815d0-109">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 <span data-ttu-id="815d0-110">Poskytuje statistiku o mechanizmu uvolňování paměti modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="815d0-110">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
 [<span data-ttu-id="815d0-111">COR_GC_THREAD_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="815d0-111">COR_GC_THREAD_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md)  
 <span data-ttu-id="815d0-112">Obsahuje statistiku jednotlivých vláken, která souvisí s uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="815d0-112">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
 [<span data-ttu-id="815d0-113">CustomDumpItem – struktura</span><span class="sxs-lookup"><span data-stu-id="815d0-113">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 <span data-ttu-id="815d0-114">Popisuje položku, která se má přidat do vlastního výpisu paměti při zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="815d0-114">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
 [<span data-ttu-id="815d0-115">MDAInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="815d0-115">MDAInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)  
 <span data-ttu-id="815d0-116">Poskytuje podrobnosti o události `Event_MDAFired`, která aktivuje vytvoření pomocníka spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="815d0-116">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
 [<span data-ttu-id="815d0-117">ModuleBindInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="815d0-117">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)  
 <span data-ttu-id="815d0-118">Obsahuje podrobné informace o odkazovaném modulu a sestavení, které ho obsahuje.</span><span class="sxs-lookup"><span data-stu-id="815d0-118">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
 [<span data-ttu-id="815d0-119">StackOverflowInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="815d0-119">StackOverflowInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/stackoverflowinfo-structure.md)  
 <span data-ttu-id="815d0-120">Ukládá typ přetečení, ke kterému došlo, a informace o výjimce, která byla vyvolána z důvodu přetečení.</span><span class="sxs-lookup"><span data-stu-id="815d0-120">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="815d0-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="815d0-121">Related Sections</span></span>  
 [<span data-ttu-id="815d0-122">Třídy typu coclass pro hostování</span><span class="sxs-lookup"><span data-stu-id="815d0-122">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [<span data-ttu-id="815d0-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="815d0-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
  
 [<span data-ttu-id="815d0-124">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="815d0-124">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="815d0-125">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="815d0-125">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
