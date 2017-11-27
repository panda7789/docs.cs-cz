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
ms.openlocfilehash: 24f6d667399d788d12d368832ed4d8638d29a0f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="hosting-structures"></a><span data-ttu-id="58ba7-102">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="58ba7-102">Hosting Structures</span></span>
<span data-ttu-id="58ba7-103">Tato část popisuje nespravované struktury, které používá rozhraní API hostování.</span><span class="sxs-lookup"><span data-stu-id="58ba7-103">This section describes the unmanaged structures that the hosting API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="58ba7-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="58ba7-104">In This Section</span></span>  
 [<span data-ttu-id="58ba7-105">Assemblybindinfo – struktura</span><span class="sxs-lookup"><span data-stu-id="58ba7-105">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)  
 <span data-ttu-id="58ba7-106">Poskytuje podrobné informace o odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="58ba7-106">Provides detailed information about the referenced assembly.</span></span>  
  
 [<span data-ttu-id="58ba7-107">Bucketparameters – struktura</span><span class="sxs-lookup"><span data-stu-id="58ba7-107">BucketParameters Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md)  
 <span data-ttu-id="58ba7-108">Ukládá název typu události a parametry pro aktuální výjimka, ke které je přidruženo k události.</span><span class="sxs-lookup"><span data-stu-id="58ba7-108">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
 [<span data-ttu-id="58ba7-109">Cor_gc_stats – struktura</span><span class="sxs-lookup"><span data-stu-id="58ba7-109">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 <span data-ttu-id="58ba7-110">Poskytuje statistiky o mechanismus kolekce paměti common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="58ba7-110">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
 [<span data-ttu-id="58ba7-111">Cor_gc_thread_stats – struktura</span><span class="sxs-lookup"><span data-stu-id="58ba7-111">COR_GC_THREAD_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md)  
 <span data-ttu-id="58ba7-112">Obsahuje vlákno statistiky týkající se uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="58ba7-112">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
 [<span data-ttu-id="58ba7-113">Customdumpitem – struktura</span><span class="sxs-lookup"><span data-stu-id="58ba7-113">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 <span data-ttu-id="58ba7-114">Popisuje položku, kterou chcete přidat do vlastní výpis v zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="58ba7-114">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
 [<span data-ttu-id="58ba7-115">Mdainfo – struktura</span><span class="sxs-lookup"><span data-stu-id="58ba7-115">MDAInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)  
 <span data-ttu-id="58ba7-116">Poskytuje podrobnosti o `Event_MDAFired` událost, která aktivuje vytvoření Pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="58ba7-116">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
 [<span data-ttu-id="58ba7-117">Modulebindinfo – struktura</span><span class="sxs-lookup"><span data-stu-id="58ba7-117">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)  
 <span data-ttu-id="58ba7-118">Poskytuje podrobné informace o odkazovaného modulu a sestavení, který jej obsahuje.</span><span class="sxs-lookup"><span data-stu-id="58ba7-118">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
 [<span data-ttu-id="58ba7-119">Stackoverflowinfo – struktura</span><span class="sxs-lookup"><span data-stu-id="58ba7-119">StackOverflowInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/stackoverflowinfo-structure.md)  
 <span data-ttu-id="58ba7-120">Uloží typ přetečení, k níž došlo a informace na výjimku, která byla vydána z důvodu přetečení.</span><span class="sxs-lookup"><span data-stu-id="58ba7-120">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="58ba7-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="58ba7-121">Related Sections</span></span>  
 [<span data-ttu-id="58ba7-122">Třídy typu coclass hostování</span><span class="sxs-lookup"><span data-stu-id="58ba7-122">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [<span data-ttu-id="58ba7-123">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="58ba7-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
  
 [<span data-ttu-id="58ba7-124">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="58ba7-124">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="58ba7-125">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="58ba7-125">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
