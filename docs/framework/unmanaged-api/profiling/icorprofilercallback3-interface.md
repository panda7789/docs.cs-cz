---
title: ICorProfilerCallback3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3
helpviewer_keywords:
- ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type:
- apiref
ms.openlocfilehash: db07e2afa64ea2bf80416e6ab8cba5a4dcdc8dcf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499672"
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="a3e42-102">ICorProfilerCallback3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a3e42-102">ICorProfilerCallback3 Interface</span></span>
<span data-ttu-id="a3e42-103">Poskytuje metody zpětného volání, které modul CLR (Common Language Runtime) používá ke komunikaci informací o stavu připojení a odpojení profileru.</span><span class="sxs-lookup"><span data-stu-id="a3e42-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a3e42-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a3e42-104">Methods</span></span>  
  
|<span data-ttu-id="a3e42-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a3e42-105">Method</span></span>|<span data-ttu-id="a3e42-106">Description</span><span class="sxs-lookup"><span data-stu-id="a3e42-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a3e42-107">InitializeForAttach – metoda</span><span class="sxs-lookup"><span data-stu-id="a3e42-107">InitializeForAttach Method</span></span>](icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="a3e42-108">Volá se modulem CLR, aby Profiler mohl po operaci připojení inicializovat svůj stav.</span><span class="sxs-lookup"><span data-stu-id="a3e42-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="a3e42-109">ProfilerAttachComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="a3e42-109">ProfilerAttachComplete Method</span></span>](icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="a3e42-110">Volá se modulem CLR k označení toho, že Profiler teď může volat metody catch.</span><span class="sxs-lookup"><span data-stu-id="a3e42-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="a3e42-111">ProfilerDetachSucceeded – metoda</span><span class="sxs-lookup"><span data-stu-id="a3e42-111">ProfilerDetachSucceeded Method</span></span>](icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="a3e42-112">Upozorní profileru, že modul CLR (Common Language Runtime) chystá uvolnění knihovny DLL profileru.</span><span class="sxs-lookup"><span data-stu-id="a3e42-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3e42-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a3e42-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3e42-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a3e42-114">Requirements</span></span>  
 <span data-ttu-id="a3e42-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3e42-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3e42-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a3e42-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a3e42-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a3e42-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3e42-118">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3e42-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3e42-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3e42-119">See also</span></span>

- [<span data-ttu-id="a3e42-120">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="a3e42-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="a3e42-121">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a3e42-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="a3e42-122">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a3e42-122">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="a3e42-123">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a3e42-123">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
