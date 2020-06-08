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
ms.openlocfilehash: 527e48d02d5267d6ae41214686c2e8c997d85dca
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499542"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a><span data-ttu-id="4f2b2-102">ICorProfilerCallback4::GetReJITParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="4f2b2-102">ICorProfilerCallback4::GetReJITParameters Method</span></span>
<span data-ttu-id="4f2b2-103">Umožňuje profileru kódu nastavit alternativní příznaky generování kódu pro nový text nové kompilované metody.</span><span class="sxs-lookup"><span data-stu-id="4f2b2-103">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f2b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f2b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f2b2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f2b2-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="4f2b2-106">pro Modul obsahující metodu, pro kterou CLR potřebuje parametry rekompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="4f2b2-106">[in] The module that contains the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `methodId`  
 <span data-ttu-id="4f2b2-107">pro `MethodDef`Metoda, pro kterou modul CLR potřebuje parametry rekompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="4f2b2-107">[in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `pFunctionControl`  
 <span data-ttu-id="4f2b2-108">pro Ukazatel na rozhraní [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) , které může Profiler použít k poskytnutí informací o rekompilaci JIT pro metodu, která je právě zkompilována.</span><span class="sxs-lookup"><span data-stu-id="4f2b2-108">[in] A pointer to an [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f2b2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4f2b2-109">Remarks</span></span>  
 <span data-ttu-id="4f2b2-110">CLR vyvolá `GetReJITParameters` zpětné volání, aby Profiler mohl určit parametry pro opětovné zkompilování dané metody.</span><span class="sxs-lookup"><span data-stu-id="4f2b2-110">The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method.</span></span> <span data-ttu-id="4f2b2-111">`GetReJITParameters`Zpětné volání je vystaveno pouze jednou funkcí. parametry zadané profilerem platí pro všechny instance této funkce.</span><span class="sxs-lookup"><span data-stu-id="4f2b2-111">The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f2b2-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4f2b2-112">Requirements</span></span>  
 <span data-ttu-id="4f2b2-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f2b2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f2b2-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4f2b2-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4f2b2-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4f2b2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f2b2-116">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f2b2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f2b2-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f2b2-117">See also</span></span>

- [<span data-ttu-id="4f2b2-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4f2b2-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="4f2b2-119">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4f2b2-119">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="4f2b2-120">JITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="4f2b2-120">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="4f2b2-121">ReJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="4f2b2-121">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)
