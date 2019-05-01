---
title: Struktury pro hostování
ms.date: 03/30/2017
helpviewer_keywords:
- hosting structures [.NET Framework]
- unmanaged structures [.NET Framework], hosting
- structures [.NET Framework hosting]
ms.assetid: 492e010f-7493-4134-9505-f7008ccdaae6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01b12af8c3c3a2f834827ff14665050e07b31467
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985592"
---
# <a name="hosting-structures"></a><span data-ttu-id="eaffa-102">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="eaffa-102">Hosting Structures</span></span>
<span data-ttu-id="eaffa-103">Tato část popisuje nespravované struktury, které používá hostujícího rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="eaffa-103">This section describes the unmanaged structures that the hosting API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eaffa-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="eaffa-104">In This Section</span></span>  
 [<span data-ttu-id="eaffa-105">AssemblyBindInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="eaffa-105">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)  
 <span data-ttu-id="eaffa-106">Poskytuje podrobné informace o odkazovaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="eaffa-106">Provides detailed information about the referenced assembly.</span></span>  
  
 [<span data-ttu-id="eaffa-107">BucketParameters – struktura</span><span class="sxs-lookup"><span data-stu-id="eaffa-107">BucketParameters Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md)  
 <span data-ttu-id="eaffa-108">Ukládá název typu události a parametry pro aktuální výjimky, které je přidruženo k události.</span><span class="sxs-lookup"><span data-stu-id="eaffa-108">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
 [<span data-ttu-id="eaffa-109">COR_GC_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="eaffa-109">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 <span data-ttu-id="eaffa-110">Poskytuje statistické údaje o mechanismu uvolnění paměti kolekce modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="eaffa-110">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
 [<span data-ttu-id="eaffa-111">COR_GC_THREAD_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="eaffa-111">COR_GC_THREAD_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md)  
 <span data-ttu-id="eaffa-112">Obsahuje vlákno statistiky týkající se uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="eaffa-112">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
 [<span data-ttu-id="eaffa-113">CustomDumpItem – struktura</span><span class="sxs-lookup"><span data-stu-id="eaffa-113">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 <span data-ttu-id="eaffa-114">Popisuje položku, kterou chcete přidat do vlastní výpisu stavu systému v hlášení chyb.</span><span class="sxs-lookup"><span data-stu-id="eaffa-114">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
 [<span data-ttu-id="eaffa-115">MDAInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="eaffa-115">MDAInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)  
 <span data-ttu-id="eaffa-116">Poskytuje podrobnosti o `Event_MDAFired` událost, která se aktivuje vytvořením Pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="eaffa-116">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
 [<span data-ttu-id="eaffa-117">ModuleBindInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="eaffa-117">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)  
 <span data-ttu-id="eaffa-118">Poskytuje podrobné informace o odkazovaného modulu a sestavení, který jej obsahuje.</span><span class="sxs-lookup"><span data-stu-id="eaffa-118">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
 [<span data-ttu-id="eaffa-119">StackOverflowInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="eaffa-119">StackOverflowInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/stackoverflowinfo-structure.md)  
 <span data-ttu-id="eaffa-120">Ukládá typu došlo k přetečení a informace o výjimce, která byla vyvolána z důvodu přetečení.</span><span class="sxs-lookup"><span data-stu-id="eaffa-120">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="eaffa-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="eaffa-121">Related Sections</span></span>  
 [<span data-ttu-id="eaffa-122">Třídy typu coclass pro hostování</span><span class="sxs-lookup"><span data-stu-id="eaffa-122">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [<span data-ttu-id="eaffa-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="eaffa-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
  
 [<span data-ttu-id="eaffa-124">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="eaffa-124">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="eaffa-125">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="eaffa-125">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
