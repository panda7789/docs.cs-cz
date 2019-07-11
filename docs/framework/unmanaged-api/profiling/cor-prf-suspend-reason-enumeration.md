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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e084bc957eca9474078ed5ca3aef0276361dbe1b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745537"
---
# <a name="corprfsuspendreason-enumeration"></a><span data-ttu-id="93505-102">COR_PRF_SUSPEND_REASON – výčet</span><span class="sxs-lookup"><span data-stu-id="93505-102">COR_PRF_SUSPEND_REASON Enumeration</span></span>
<span data-ttu-id="93505-103">Označuje, že je pozastavený, modul runtime důvod.</span><span class="sxs-lookup"><span data-stu-id="93505-103">Indicates the reason that the runtime is suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93505-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93505-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="93505-105">Členové</span><span class="sxs-lookup"><span data-stu-id="93505-105">Members</span></span>  
  
|<span data-ttu-id="93505-106">Člen</span><span class="sxs-lookup"><span data-stu-id="93505-106">Member</span></span>|<span data-ttu-id="93505-107">Popis</span><span class="sxs-lookup"><span data-stu-id="93505-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|<span data-ttu-id="93505-108">Modul runtime je pozastaven z neznámého důvodu nezdařila.</span><span class="sxs-lookup"><span data-stu-id="93505-108">The runtime is suspended for an unspecified reason.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|<span data-ttu-id="93505-109">Modul runtime je pozastavený, k plnění požadavků kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="93505-109">The runtime is suspended to service a garbage collection request.</span></span><br /><br /> <span data-ttu-id="93505-110">Zpětná volání související s kolekcí uvolnění paměti, ke kterým dochází mezi [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) a [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="93505-110">The garbage collection-related callbacks occur between the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|<span data-ttu-id="93505-111">Modul runtime je pozastavený, tak, aby `AppDomain` můžete vypnout.</span><span class="sxs-lookup"><span data-stu-id="93505-111">The runtime is suspended so that an `AppDomain` can be shut down.</span></span><br /><br /> <span data-ttu-id="93505-112">Modul runtime je pozastaven, modul runtime se určit, která vlákna jsou v `AppDomain` , který je právě vypnout a nastavit je na zrušení po jejich obnovení.</span><span class="sxs-lookup"><span data-stu-id="93505-112">While the runtime is suspended, the runtime will determine which threads are in the `AppDomain` that is being shut down and set them to abort when they resume.</span></span> <span data-ttu-id="93505-113">Neexistují žádné `AppDomain`-konkrétní zpětná volání během této doby pozastavení.</span><span class="sxs-lookup"><span data-stu-id="93505-113">There are no `AppDomain`-specific callbacks during this suspension.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|<span data-ttu-id="93505-114">Modul runtime je pozastavený, aby mohla probíhat pitching kódu.</span><span class="sxs-lookup"><span data-stu-id="93505-114">The runtime is suspended so that code pitching can occur.</span></span><br /><br /> <span data-ttu-id="93505-115">Kód pitching vyplývá, pouze pokud kompilátor just-in-time (JIT) je aktivní s kódem pitching povolené.</span><span class="sxs-lookup"><span data-stu-id="93505-115">Code pitching ensues only when the just-in-time (JIT) compiler is active with code pitching enabled.</span></span> <span data-ttu-id="93505-116">Kód pitching zpětná volání, ke kterým dochází mezi `ICorProfilerCallback::RuntimeSuspendFinished` a `ICorProfilerCallback::RuntimeResumeStarted` zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="93505-116">Code pitching callbacks occur between the `ICorProfilerCallback::RuntimeSuspendFinished` and `ICorProfilerCallback::RuntimeResumeStarted` callbacks.</span></span> <span data-ttu-id="93505-117">**Poznámka:**  CLR JIT není představení funkcí v rozhraní .NET Framework verze 2.0, takže tato hodnota se používá ve verzi 2.0.</span><span class="sxs-lookup"><span data-stu-id="93505-117">**Note:**  The CLR JIT does not pitch functions in the .NET Framework version 2.0, so this value is not used in 2.0.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|<span data-ttu-id="93505-118">Modul runtime je pozastavený, takže můžete vypnout.</span><span class="sxs-lookup"><span data-stu-id="93505-118">The runtime is suspended so that it can shut down.</span></span> <span data-ttu-id="93505-119">Se musí pozastavit všechna vlákna do dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="93505-119">It must suspend all threads to complete the operation.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|<span data-ttu-id="93505-120">Modul runtime je pozastaven vnitroprocesové ladění.</span><span class="sxs-lookup"><span data-stu-id="93505-120">The runtime is suspended for in-process debugging.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|<span data-ttu-id="93505-121">Modul runtime je pozastavený, příprava pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="93505-121">The runtime is suspended to prepare for a garbage collection.</span></span>|  
|`COR_PRF_SUSPEND_FOR_REJIT`|<span data-ttu-id="93505-122">Modul runtime je pozastaven rekompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="93505-122">The runtime is suspended for JIT recompilation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93505-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93505-123">Remarks</span></span>  
 <span data-ttu-id="93505-124">Všechna vlákna modulu runtime, které jsou v nespravovaném kódu povoleno spuštění, dokud se pokusí znovu zadat modulu runtime, v tomto okamžiku se bude také být pozastaveno, dokud modul runtime bude pokračovat dál.</span><span class="sxs-lookup"><span data-stu-id="93505-124">All runtime threads that are in unmanaged code are permitted to continue running until they try to re-enter the runtime, at which point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="93505-125">To platí i pro nová vlákna, které zadejte modul runtime.</span><span class="sxs-lookup"><span data-stu-id="93505-125">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="93505-126">Všechna vlákna v modulu runtime jsou pozastavena okamžitě, když jsou v paralelní kód nebo dotaz, pozastavit, když dosáhnou paralelní kód.</span><span class="sxs-lookup"><span data-stu-id="93505-126">All threads within the runtime are either suspended immediately if they are in interruptible code, or asked to suspend when they do reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93505-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="93505-127">Requirements</span></span>  
 <span data-ttu-id="93505-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93505-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93505-129">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="93505-129">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="93505-130">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93505-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93505-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93505-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93505-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93505-132">See also</span></span>

- [<span data-ttu-id="93505-133">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="93505-133">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
