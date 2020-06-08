---
title: ICorProfilerCallback3::ProfilerAttachComplete – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
ms.openlocfilehash: bcc938ff9322fca4f45366fdc695e0c3901484b5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499659"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="9ec9d-102">ICorProfilerCallback3::ProfilerAttachComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="9ec9d-102">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>
<span data-ttu-id="9ec9d-103">Volá se modulem CLR (Common Language Runtime), který označuje, že Profiler teď může volat metody Catch [ICorProfilerInfo3:: EnumJITedFunctions –](icorprofilerinfo3-enumjitedfunctions-method.md) a [ICorProfilerInfo3:: enummodules –](icorprofilerinfo3-enummodules-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9ec9d-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ec9d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ec9d-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="9ec9d-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ec9d-105">Remarks</span></span>  
 <span data-ttu-id="9ec9d-106">`ProfilerAttachComplete`Zpětné volání je vystaveno po volání metody [ICorProfilerCallback3:: InitializeForAttach –](icorprofilercallback3-initializeforattach-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9ec9d-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="9ec9d-107">Označuje následující:</span><span class="sxs-lookup"><span data-stu-id="9ec9d-107">It indicates the following:</span></span>  
  
- <span data-ttu-id="9ec9d-108">Zpětná volání, která požadoval Profiler, byly `InitializeForAttach` aktivovány.</span><span class="sxs-lookup"><span data-stu-id="9ec9d-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
- <span data-ttu-id="9ec9d-109">Profiler teď může provádět zachytávání u přidružených ID, aniž by se museli zabývat informacemi o chybějících oznámeních.</span><span class="sxs-lookup"><span data-stu-id="9ec9d-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="9ec9d-110">CLR ignoruje návratovou hodnotu z tohoto zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="9ec9d-110">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ec9d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ec9d-111">Requirements</span></span>  
 <span data-ttu-id="9ec9d-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ec9d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ec9d-113">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9ec9d-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9ec9d-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9ec9d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ec9d-115">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ec9d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ec9d-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ec9d-116">See also</span></span>

- [<span data-ttu-id="9ec9d-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ec9d-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="9ec9d-118">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ec9d-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="9ec9d-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="9ec9d-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="9ec9d-120">Profilace</span><span class="sxs-lookup"><span data-stu-id="9ec9d-120">Profiling</span></span>](index.md)
