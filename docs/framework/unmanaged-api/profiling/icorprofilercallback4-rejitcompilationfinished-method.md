---
title: ICorProfilerCallback4::ReJITCompilationFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished
helpviewer_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished method [.NET Framework profiling]
- ReJITCompilationFinished method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 3b5cff02-2005-44eb-a2bc-50214c4b0e1d
topic_type:
- apiref
ms.openlocfilehash: e010a49dabd3b44602136e70b4c5524a68bdd9e2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865204"
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a><span data-ttu-id="b8efc-102">ICorProfilerCallback4::ReJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="b8efc-102">ICorProfilerCallback4::ReJITCompilationFinished Method</span></span>
<span data-ttu-id="b8efc-103">Upozorní profileru, že kompilátor JIT (just-in-time) dokončil opětovné kompilování funkce.</span><span class="sxs-lookup"><span data-stu-id="b8efc-103">Notifies the profiler that the just-in-time (JIT) compiler has finished recompiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8efc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8efc-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8efc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8efc-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b8efc-106">pro ID funkce, která byla znovu zkompilována.</span><span class="sxs-lookup"><span data-stu-id="b8efc-106">[in] The ID of the function that was recompiled.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="b8efc-107">pro Identita funkce Rekompilované JIT.</span><span class="sxs-lookup"><span data-stu-id="b8efc-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="b8efc-108">pro Hodnota, která označuje, zda byla opětovná kompilace JIT úspěšná.</span><span class="sxs-lookup"><span data-stu-id="b8efc-108">[in] A value that indicates whether the JIT recompilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="b8efc-109">[in] `true` označuje, že blokování může způsobit, že modul runtime počká, než se volající vlákno vrátí z tohoto zpětného volání. `false` k označení, že blokování nebude mít vliv na operaci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b8efc-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  
  
 <span data-ttu-id="b8efc-110">Hodnota `true` nepoškozuje modul runtime, ale může ovlivnit výsledky profilace.</span><span class="sxs-lookup"><span data-stu-id="b8efc-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8efc-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b8efc-111">Requirements</span></span>  
 <span data-ttu-id="b8efc-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8efc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8efc-113">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b8efc-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b8efc-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b8efc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8efc-115">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8efc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8efc-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8efc-116">See also</span></span>

- [<span data-ttu-id="b8efc-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b8efc-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b8efc-118">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b8efc-118">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="b8efc-119">JITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="b8efc-119">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="b8efc-120">ReJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="b8efc-120">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)
