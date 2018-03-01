---
title: "COR_PRF_SUSPEND_REASON – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- COR_PRF_SUSPEND_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SUSPEND_REASON
helpviewer_keywords:
- COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 713360b3cdc30ce7bca3e0df115016d66e59b0df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corprfsuspendreason-enumeration"></a><span data-ttu-id="abc3d-102">COR_PRF_SUSPEND_REASON – výčet</span><span class="sxs-lookup"><span data-stu-id="abc3d-102">COR_PRF_SUSPEND_REASON Enumeration</span></span>
<span data-ttu-id="abc3d-103">Určuje, z důvodu, že je pozastaveno modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="abc3d-103">Indicates the reason that the runtime is suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abc3d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abc3d-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_SUSPEND_OTHER                   = 0x00,  
    COR_PRF_SUSPEND_FOR_GC                  = 0x01,  
    COR_PRF_SUSPEND_FOR_APPDOMAIN_SHUTDOWN  = 0x02,  
    COR_PRF_SUSPEND_FOR_CODE_PITCHING       = 0x03,  
    COR_PRF_SUSPEND_FOR_SHUTDOWN            = 0x04,  
    COR_PRF_SUSPEND_FOR_INPROC_DEBUGGER     = 0x06,  
    COR_PRF_SUSPEND_FOR_GC_PREP             = 0x07,    COR_PRF_SUSPEND_FOR_REJIT               = 8  
} COR_PRF_SUSPEND_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="abc3d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="abc3d-105">Members</span></span>  
  
|<span data-ttu-id="abc3d-106">Člen</span><span class="sxs-lookup"><span data-stu-id="abc3d-106">Member</span></span>|<span data-ttu-id="abc3d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="abc3d-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|<span data-ttu-id="abc3d-108">Modul runtime je pozastaven z neznámého důvodu.</span><span class="sxs-lookup"><span data-stu-id="abc3d-108">The runtime is suspended for an unspecified reason.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|<span data-ttu-id="abc3d-109">Modul runtime pozastavený, aby služba žádost kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="abc3d-109">The runtime is suspended to service a garbage collection request.</span></span><br /><br /> <span data-ttu-id="abc3d-110">Zpětná volání související s kolekcí paměti dojde k mezi [icorprofilercallback::runtimesuspendfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) a [icorprofilercallback::runtimeresumestarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="abc3d-110">The garbage collection-related callbacks occur between the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|<span data-ttu-id="abc3d-111">Modul runtime je pozastaveno, aby `AppDomain` může být vypnut.</span><span class="sxs-lookup"><span data-stu-id="abc3d-111">The runtime is suspended so that an `AppDomain` can be shut down.</span></span><br /><br /> <span data-ttu-id="abc3d-112">Modul runtime pozastaven, modul runtime určí vláken, které jsou v `AppDomain` který je právě vypnout a nastavit je k přerušení po jejich obnovení.</span><span class="sxs-lookup"><span data-stu-id="abc3d-112">While the runtime is suspended, the runtime will determine which threads are in the `AppDomain` that is being shut down and set them to abort when they resume.</span></span> <span data-ttu-id="abc3d-113">Neexistují žádné `AppDomain`-konkrétní zpětná volání během této doby pozastavení.</span><span class="sxs-lookup"><span data-stu-id="abc3d-113">There are no `AppDomain`-specific callbacks during this suspension.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|<span data-ttu-id="abc3d-114">Modul runtime je pozastaven, tak, aby pitching kódu může dojít.</span><span class="sxs-lookup"><span data-stu-id="abc3d-114">The runtime is suspended so that code pitching can occur.</span></span><br /><br /> <span data-ttu-id="abc3d-115">Kód pitching vyplývá, pouze když kompilátoru za běhu (JIT) je aktivní s kód pitching povolena.</span><span class="sxs-lookup"><span data-stu-id="abc3d-115">Code pitching ensues only when the just-in-time (JIT) compiler is active with code pitching enabled.</span></span> <span data-ttu-id="abc3d-116">Kód pitching zpětná volání dojít mezi `ICorProfilerCallback::RuntimeSuspendFinished` a `ICorProfilerCallback::RuntimeResumeStarted` zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="abc3d-116">Code pitching callbacks occur between the `ICorProfilerCallback::RuntimeSuspendFinished` and `ICorProfilerCallback::RuntimeResumeStarted` callbacks.</span></span> <span data-ttu-id="abc3d-117">**Poznámka:** CLR JIT není pro představení funkce v rozhraní .NET Framework verze 2.0, tak tato hodnota se nepoužívá v 2.0.</span><span class="sxs-lookup"><span data-stu-id="abc3d-117">**Note:**  The CLR JIT does not pitch functions in the .NET Framework version 2.0, so this value is not used in 2.0.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|<span data-ttu-id="abc3d-118">Modul runtime je pozastaven, tak, aby ho vypnout.</span><span class="sxs-lookup"><span data-stu-id="abc3d-118">The runtime is suspended so that it can shut down.</span></span> <span data-ttu-id="abc3d-119">Musíte ho pozastavit všechna vlákna k dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="abc3d-119">It must suspend all threads to complete the operation.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|<span data-ttu-id="abc3d-120">Modul runtime je pozastavená v procesu ladění.</span><span class="sxs-lookup"><span data-stu-id="abc3d-120">The runtime is suspended for in-process debugging.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|<span data-ttu-id="abc3d-121">Příprava pro kolekci paměti je pozastaven modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="abc3d-121">The runtime is suspended to prepare for a garbage collection.</span></span>|  
|`COR_PRF_SUSPEND_FOR_REJIT`|<span data-ttu-id="abc3d-122">Modul runtime je pozastaven pro opětovnou kompilaci JIT.</span><span class="sxs-lookup"><span data-stu-id="abc3d-122">The runtime is suspended for JIT recompilation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abc3d-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="abc3d-123">Remarks</span></span>  
 <span data-ttu-id="abc3d-124">Všechna vlákna modulu runtime, které jsou v nespravovaném kódu je povoleno dále běžet až do snaží znovu zadat modulu runtime v bod, který se bude také pozastavuje, dokud nebude obnoví modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="abc3d-124">All runtime threads that are in unmanaged code are permitted to continue running until they try to re-enter the runtime, at which point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="abc3d-125">To platí také pro nové vláken, která zadejte modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="abc3d-125">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="abc3d-126">Všechna vlákna v modulu runtime jsou buď okamžitě pozastaveno, pokud se dá přerušit kódu nebo požádáni, abyste pozastavit po uplynutí přerušitelné kódu.</span><span class="sxs-lookup"><span data-stu-id="abc3d-126">All threads within the runtime are either suspended immediately if they are in interruptible code, or asked to suspend when they do reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abc3d-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="abc3d-127">Requirements</span></span>  
 <span data-ttu-id="abc3d-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abc3d-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abc3d-129">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="abc3d-129">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="abc3d-130">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abc3d-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abc3d-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abc3d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abc3d-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="abc3d-132">See Also</span></span>  
 [<span data-ttu-id="abc3d-133">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="abc3d-133">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
