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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6a181ca2da8385107d63cd94ea832846c4211ad5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650387"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="98789-102">ICorProfilerCallback3::ProfilerAttachComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="98789-102">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>
<span data-ttu-id="98789-103">Volá se, modulem common language runtime (CLR), která označuje, že profiler nyní volat [icorprofilerinfo3::enumjitedfunctions –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) a [ICorProfilerInfo3::EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) můžete projít metody.</span><span class="sxs-lookup"><span data-stu-id="98789-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98789-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98789-104">Syntax</span></span>  
  
```  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="98789-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="98789-105">Remarks</span></span>  
 <span data-ttu-id="98789-106">`ProfilerAttachComplete` Zpětného volání je vydané po [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="98789-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="98789-107">Označuje následující:</span><span class="sxs-lookup"><span data-stu-id="98789-107">It indicates the following:</span></span>  
  
- <span data-ttu-id="98789-108">Zpětná volání, které bylo vyžádáno profilerem v `InitializeForAttach` aktivaci.</span><span class="sxs-lookup"><span data-stu-id="98789-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
- <span data-ttu-id="98789-109">Profiler teď můžete provádět zachytávání přidružené identifikátory bez obavy z chybějícího upozornění.</span><span class="sxs-lookup"><span data-stu-id="98789-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="98789-110">Modul CLR bude ignorovat návratovou hodnotu z této zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="98789-110">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98789-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="98789-111">Requirements</span></span>  
 <span data-ttu-id="98789-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98789-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98789-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="98789-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="98789-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98789-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98789-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98789-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98789-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98789-116">See also</span></span>

- [<span data-ttu-id="98789-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="98789-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="98789-118">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="98789-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="98789-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="98789-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="98789-120">Profilace</span><span class="sxs-lookup"><span data-stu-id="98789-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
