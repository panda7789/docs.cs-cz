---
title: ICorProfilerCallback4::GetReJITParameters – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.GetReJITParameters
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::GetReJITParameters
helpviewer_keywords:
- ICorProfilerCallback4::GetReJITParameters method [.NET Framework profiling]
- GetReJITParameters method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 0e9bfe07-9f20-498c-b568-9017c8f6056c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7aae292daefe9333585a50d1d8c9ce49b1008cd9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470780"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a><span data-ttu-id="c1a56-102">ICorProfilerCallback4::GetReJITParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="c1a56-102">ICorProfilerCallback4::GetReJITParameters Method</span></span>
<span data-ttu-id="c1a56-103">Umožňuje profileru kódu nastavit alternativní kód generování příznaky pro nové tělo překompilovanou metody.</span><span class="sxs-lookup"><span data-stu-id="c1a56-103">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1a56-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1a56-104">Syntax</span></span>  
  
```  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1a56-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1a56-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="c1a56-106">[in] Modul, který obsahuje metodu, pro které modul CLR musí parametry rekompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="c1a56-106">[in] The module that contains the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `methodId`  
 <span data-ttu-id="c1a56-107">[in] `MethodDef` Metody, pro které modul CLR musí parametry rekompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="c1a56-107">[in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `pFunctionControl`  
 <span data-ttu-id="c1a56-108">[in] Ukazatel [icorprofilerfunctioncontrol –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) rozhraní, které profileru můžete použít k poskytnutí informací rekompilace JIT pro metodu se znovu zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="c1a56-108">[in] A pointer to an [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1a56-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c1a56-109">Remarks</span></span>  
 <span data-ttu-id="c1a56-110">Problémy s CLR `GetReJITParameters` zpětné volání tak, aby profileru můžete zadat parametry pro opětovné kompilaci dané metody.</span><span class="sxs-lookup"><span data-stu-id="c1a56-110">The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method.</span></span> <span data-ttu-id="c1a56-111">`GetReJITParameters` Zpětného volání je vydaný pouze jednou pro každou funkci; parametry zadané pomocí profileru platí pro všechny instance této funkce.</span><span class="sxs-lookup"><span data-stu-id="c1a56-111">The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1a56-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c1a56-112">Requirements</span></span>  
 <span data-ttu-id="c1a56-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1a56-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1a56-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c1a56-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c1a56-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1a56-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1a56-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1a56-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1a56-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1a56-117">See also</span></span>
- [<span data-ttu-id="c1a56-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1a56-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="c1a56-119">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1a56-119">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="c1a56-120">JITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="c1a56-120">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="c1a56-121">ReJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="c1a56-121">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
