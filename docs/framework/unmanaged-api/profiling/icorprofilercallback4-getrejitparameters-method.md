---
title: "ICorProfilerCallback4::GetReJITParameters – metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 03e5440fbd016f52642a5626b0cf0b82e7ecea45
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback4getrejitparameters-method"></a><span data-ttu-id="c011c-102">ICorProfilerCallback4::GetReJITParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="c011c-102">ICorProfilerCallback4::GetReJITParameters Method</span></span>
<span data-ttu-id="c011c-103">Umožňuje profileru kódu nastavit alternativní kód pro nový text Rekompilované metoda příznaky generace.</span><span class="sxs-lookup"><span data-stu-id="c011c-103">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c011c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c011c-104">Syntax</span></span>  
  
```  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c011c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c011c-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="c011c-106">[v] Modul, který obsahuje metodu, pro niž je modulu CLR JIT rekompilace parametry.</span><span class="sxs-lookup"><span data-stu-id="c011c-106">[in] The module that contains the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `methodId`  
 <span data-ttu-id="c011c-107">[v] `MethodDef` Metody, pro niž je modulu CLR JIT rekompilace parametry.</span><span class="sxs-lookup"><span data-stu-id="c011c-107">[in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `pFunctionControl`  
 <span data-ttu-id="c011c-108">[v] Ukazatel na [icorprofilerfunctioncontrol –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) rozhraní, které profileru můžete použít k zadání informací o opětovnou kompilaci JIT pro metodu se překompilovat.</span><span class="sxs-lookup"><span data-stu-id="c011c-108">[in] A pointer to an [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c011c-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c011c-109">Remarks</span></span>  
 <span data-ttu-id="c011c-110">Problémy CLR `GetReJITParameters` zpětného volání, aby profileru můžete zadat parametry pro nutnosti rekompilace dané metody.</span><span class="sxs-lookup"><span data-stu-id="c011c-110">The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method.</span></span> <span data-ttu-id="c011c-111">`GetReJITParameters` Zpětné volání se objeví pouze jednou za funkce; parametry poskytl profileru platí pro všechny instance této funkce.</span><span class="sxs-lookup"><span data-stu-id="c011c-111">The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c011c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c011c-112">Requirements</span></span>  
 <span data-ttu-id="c011c-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c011c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c011c-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c011c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c011c-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c011c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c011c-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c011c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c011c-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="c011c-117">See Also</span></span>  
 [<span data-ttu-id="c011c-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c011c-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="c011c-119">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c011c-119">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [<span data-ttu-id="c011c-120">JITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="c011c-120">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)  
 [<span data-ttu-id="c011c-121">ReJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="c011c-121">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
