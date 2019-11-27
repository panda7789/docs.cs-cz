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
ms.openlocfilehash: d81d7275d197de1dfc99b135377459f509c2651f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439434"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a><span data-ttu-id="f13f8-102">ICorProfilerCallback4::GetReJITParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="f13f8-102">ICorProfilerCallback4::GetReJITParameters Method</span></span>
<span data-ttu-id="f13f8-103">Umožňuje profileru kódu nastavit alternativní příznaky generování kódu pro nový text nové kompilované metody.</span><span class="sxs-lookup"><span data-stu-id="f13f8-103">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f13f8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f13f8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f13f8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f13f8-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="f13f8-106">pro Modul obsahující metodu, pro kterou CLR potřebuje parametry rekompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="f13f8-106">[in] The module that contains the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `methodId`  
 <span data-ttu-id="f13f8-107">pro `MethodDef` metody, pro kterou modul CLR potřebuje parametry rekompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="f13f8-107">[in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `pFunctionControl`  
 <span data-ttu-id="f13f8-108">pro Ukazatel na rozhraní [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) , které může Profiler použít k poskytnutí informací o rekompilaci JIT pro metodu, která je právě zkompilována.</span><span class="sxs-lookup"><span data-stu-id="f13f8-108">[in] A pointer to an [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f13f8-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f13f8-109">Remarks</span></span>  
 <span data-ttu-id="f13f8-110">CLR vydá `GetReJITParameters` zpětného volání, aby Profiler mohl určit parametry pro opětovné zkompilování dané metody.</span><span class="sxs-lookup"><span data-stu-id="f13f8-110">The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method.</span></span> <span data-ttu-id="f13f8-111">Zpětné volání `GetReJITParameters` je vystaveno pouze jednou pro funkci; parametry zadané profilerem se vztahují na všechny instance této funkce.</span><span class="sxs-lookup"><span data-stu-id="f13f8-111">The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f13f8-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f13f8-112">Requirements</span></span>  
 <span data-ttu-id="f13f8-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f13f8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f13f8-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f13f8-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f13f8-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f13f8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f13f8-116">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f13f8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f13f8-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f13f8-117">See also</span></span>

- [<span data-ttu-id="f13f8-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f13f8-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="f13f8-119">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f13f8-119">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="f13f8-120">JITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="f13f8-120">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="f13f8-121">ReJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="f13f8-121">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
