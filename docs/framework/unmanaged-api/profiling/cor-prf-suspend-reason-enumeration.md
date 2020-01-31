---
title: COR_PRF_SUSPEND_REASON – výčet
ms.date: 03/30/2017
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
ms.openlocfilehash: 1036ecbdb735b95c0ad6897c1545e3bd8cb6c3a9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867071"
---
# <a name="cor_prf_suspend_reason-enumeration"></a><span data-ttu-id="116f4-102">COR_PRF_SUSPEND_REASON – výčet</span><span class="sxs-lookup"><span data-stu-id="116f4-102">COR_PRF_SUSPEND_REASON Enumeration</span></span>
<span data-ttu-id="116f4-103">Označuje důvod, proč je modul runtime pozastaven.</span><span class="sxs-lookup"><span data-stu-id="116f4-103">Indicates the reason that the runtime is suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="116f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="116f4-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="116f4-105">Členové</span><span class="sxs-lookup"><span data-stu-id="116f4-105">Members</span></span>  
  
|<span data-ttu-id="116f4-106">Člen</span><span class="sxs-lookup"><span data-stu-id="116f4-106">Member</span></span>|<span data-ttu-id="116f4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="116f4-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|<span data-ttu-id="116f4-108">Modul runtime je pozastaven z nespecifikovaného důvodu.</span><span class="sxs-lookup"><span data-stu-id="116f4-108">The runtime is suspended for an unspecified reason.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|<span data-ttu-id="116f4-109">Modul runtime je pozastaven na obsluhu žádosti o uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="116f4-109">The runtime is suspended to service a garbage collection request.</span></span><br /><br /> <span data-ttu-id="116f4-110">Zpětná volání související s uvolňováním paměti nastávají mezi zpětnými voláními [ICorProfilerCallback:: RuntimeSuspendFinished –](icorprofilercallback-runtimesuspendfinished-method.md) a [ICorProfilerCallback:: RuntimeResumeStarted –](icorprofilercallback-runtimeresumestarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="116f4-110">The garbage collection-related callbacks occur between the [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) and [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|<span data-ttu-id="116f4-111">Modul runtime je pozastaven, aby bylo možné vypnout `AppDomain`.</span><span class="sxs-lookup"><span data-stu-id="116f4-111">The runtime is suspended so that an `AppDomain` can be shut down.</span></span><br /><br /> <span data-ttu-id="116f4-112">I když je modul runtime pozastaven, modul runtime určí, která vlákna jsou v `AppDomain`, která se vypíná a která se nastaví pro přerušení při obnovení.</span><span class="sxs-lookup"><span data-stu-id="116f4-112">While the runtime is suspended, the runtime will determine which threads are in the `AppDomain` that is being shut down and set them to abort when they resume.</span></span> <span data-ttu-id="116f4-113">Během tohoto pozastavení neexistují žádná zpětná volání specifická pro `AppDomain`.</span><span class="sxs-lookup"><span data-stu-id="116f4-113">There are no `AppDomain`-specific callbacks during this suspension.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|<span data-ttu-id="116f4-114">Modul runtime je pozastaven, aby mohlo dojít k rozteči kódu.</span><span class="sxs-lookup"><span data-stu-id="116f4-114">The runtime is suspended so that code pitching can occur.</span></span><br /><br /> <span data-ttu-id="116f4-115">Rozteč kódu platí pouze v případě, že je kompilátor JIT (just-in-time) aktivní se zapnutým příznakem pro rozteč kódu.</span><span class="sxs-lookup"><span data-stu-id="116f4-115">Code pitching ensues only when the just-in-time (JIT) compiler is active with code pitching enabled.</span></span> <span data-ttu-id="116f4-116">Zpětná volání pro rozteč kódu se vyskytují mezi `ICorProfilerCallback::RuntimeSuspendFinished` a `ICorProfilerCallback::RuntimeResumeStarted` zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="116f4-116">Code pitching callbacks occur between the `ICorProfilerCallback::RuntimeSuspendFinished` and `ICorProfilerCallback::RuntimeResumeStarted` callbacks.</span></span> <span data-ttu-id="116f4-117">**Poznámka:**  Kompilátor JIT CLR nemění funkce v .NET Framework verze 2,0, takže se tato hodnota nepoužívá v 2,0.</span><span class="sxs-lookup"><span data-stu-id="116f4-117">**Note:**  The CLR JIT does not pitch functions in the .NET Framework version 2.0, so this value is not used in 2.0.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|<span data-ttu-id="116f4-118">Modul runtime je pozastaven, aby mohl být vypnut.</span><span class="sxs-lookup"><span data-stu-id="116f4-118">The runtime is suspended so that it can shut down.</span></span> <span data-ttu-id="116f4-119">Aby bylo možné operaci dokončit, je nutné pozastavit všechna vlákna.</span><span class="sxs-lookup"><span data-stu-id="116f4-119">It must suspend all threads to complete the operation.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|<span data-ttu-id="116f4-120">Modul runtime je pozastaven pro vnitroprocesové ladění.</span><span class="sxs-lookup"><span data-stu-id="116f4-120">The runtime is suspended for in-process debugging.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|<span data-ttu-id="116f4-121">Modul runtime je pozastaven pro přípravu na uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="116f4-121">The runtime is suspended to prepare for a garbage collection.</span></span>|  
|`COR_PRF_SUSPEND_FOR_REJIT`|<span data-ttu-id="116f4-122">Modul runtime je pozastaven pro rekompilaci JIT.</span><span class="sxs-lookup"><span data-stu-id="116f4-122">The runtime is suspended for JIT recompilation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="116f4-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="116f4-123">Remarks</span></span>  
 <span data-ttu-id="116f4-124">Všechna vlákna modulu runtime, která jsou v nespravovaném kódu, mohou pokračovat v běhu, dokud se nepokusí znovu zadat modul runtime. v takovém případě budou také pozastaveny, dokud modul runtime nebude pokračovat.</span><span class="sxs-lookup"><span data-stu-id="116f4-124">All runtime threads that are in unmanaged code are permitted to continue running until they try to re-enter the runtime, at which point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="116f4-125">To platí také pro nová vlákna, která vstupují do modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="116f4-125">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="116f4-126">Všechna vlákna v modulu runtime jsou okamžitě pozastavena, pokud jsou v kódu přerušitelné, nebo se po zobrazení výzvy k tomu, že mají přístup ke kódu přerušitelné, pozastaví.</span><span class="sxs-lookup"><span data-stu-id="116f4-126">All threads within the runtime are either suspended immediately if they are in interruptible code, or asked to suspend when they do reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="116f4-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="116f4-127">Requirements</span></span>  
 <span data-ttu-id="116f4-128">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="116f4-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="116f4-129">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="116f4-129">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="116f4-130">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="116f4-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="116f4-131">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="116f4-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="116f4-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="116f4-132">See also</span></span>

- [<span data-ttu-id="116f4-133">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="116f4-133">Profiling Enumerations</span></span>](profiling-enumerations.md)
