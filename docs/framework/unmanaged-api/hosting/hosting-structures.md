---
title: "Struktury pro hostování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- hosting structures [.NET Framework]
- unmanaged structures [.NET Framework], hosting
- structures [.NET Framework hosting]
ms.assetid: 492e010f-7493-4134-9505-f7008ccdaae6
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e59353272856525b7d72f322694d15a42ab7b32
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-structures"></a><span data-ttu-id="a1b53-102">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="a1b53-102">Hosting Structures</span></span>
<span data-ttu-id="a1b53-103">Tato část popisuje nespravované struktury, které používá rozhraní API hostování.</span><span class="sxs-lookup"><span data-stu-id="a1b53-103">This section describes the unmanaged structures that the hosting API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a1b53-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a1b53-104">In This Section</span></span>  
 [<span data-ttu-id="a1b53-105">AssemblyBindInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="a1b53-105">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)  
 <span data-ttu-id="a1b53-106">Poskytuje podrobné informace o odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="a1b53-106">Provides detailed information about the referenced assembly.</span></span>  
  
 [<span data-ttu-id="a1b53-107">BucketParameters – struktura</span><span class="sxs-lookup"><span data-stu-id="a1b53-107">BucketParameters Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md)  
 <span data-ttu-id="a1b53-108">Ukládá název typu události a parametry pro aktuální výjimka, ke které je přidruženo k události.</span><span class="sxs-lookup"><span data-stu-id="a1b53-108">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
 [<span data-ttu-id="a1b53-109">COR_GC_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="a1b53-109">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 <span data-ttu-id="a1b53-110">Poskytuje statistiky o mechanismus kolekce paměti common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="a1b53-110">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
 [<span data-ttu-id="a1b53-111">COR_GC_THREAD_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="a1b53-111">COR_GC_THREAD_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md)  
 <span data-ttu-id="a1b53-112">Obsahuje vlákno statistiky týkající se uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="a1b53-112">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
 [<span data-ttu-id="a1b53-113">CustomDumpItem – struktura</span><span class="sxs-lookup"><span data-stu-id="a1b53-113">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 <span data-ttu-id="a1b53-114">Popisuje položku, kterou chcete přidat do vlastní výpis v zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="a1b53-114">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
 [<span data-ttu-id="a1b53-115">MDAInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="a1b53-115">MDAInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)  
 <span data-ttu-id="a1b53-116">Poskytuje podrobnosti o `Event_MDAFired` událost, která aktivuje vytvoření Pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="a1b53-116">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
 [<span data-ttu-id="a1b53-117">ModuleBindInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="a1b53-117">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)  
 <span data-ttu-id="a1b53-118">Poskytuje podrobné informace o odkazovaného modulu a sestavení, který jej obsahuje.</span><span class="sxs-lookup"><span data-stu-id="a1b53-118">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
 [<span data-ttu-id="a1b53-119">StackOverflowInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="a1b53-119">StackOverflowInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/stackoverflowinfo-structure.md)  
 <span data-ttu-id="a1b53-120">Uloží typ přetečení, k níž došlo a informace na výjimku, která byla vydána z důvodu přetečení.</span><span class="sxs-lookup"><span data-stu-id="a1b53-120">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a1b53-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="a1b53-121">Related Sections</span></span>  
 [<span data-ttu-id="a1b53-122">Třídy typu coclass pro hostování</span><span class="sxs-lookup"><span data-stu-id="a1b53-122">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [<span data-ttu-id="a1b53-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="a1b53-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
  
 [<span data-ttu-id="a1b53-124">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="a1b53-124">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="a1b53-125">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="a1b53-125">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
