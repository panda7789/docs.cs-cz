---
title: ICorProfilerCallback4::ReJITError – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITError
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66f152279a21f28b54acebbf0be7c65bb73efa70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767472"
---
# <a name="icorprofilercallback4rejiterror-method"></a><span data-ttu-id="2f2f6-102">ICorProfilerCallback4::ReJITError – metoda</span><span class="sxs-lookup"><span data-stu-id="2f2f6-102">ICorProfilerCallback4::ReJITError Method</span></span>
<span data-ttu-id="2f2f6-103">Oznámí profileru, že kompilátor just-in-time (JIT) došlo k chybě v procesu opětovnou kompilaci.</span><span class="sxs-lookup"><span data-stu-id="2f2f6-103">Notifies the profiler that the just-in-time (JIT) compiler encountered an error in the recompilation process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f2f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f2f6-104">Syntax</span></span>  
  
```  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f2f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f2f6-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="2f2f6-106">[in] `ModuleID` Ve které byl proveden pokus o opětovnou kompilaci se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="2f2f6-106">[in] The `ModuleID` in which the failed recompilation attempt was made.</span></span>  
  
 `methodId`  
 <span data-ttu-id="2f2f6-107">[in] `MethodDef` Metody, na kterém byl proveden pokus o opětovnou kompilaci se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="2f2f6-107">[in] The `MethodDef` of the method on which the failed recompilation attempt was made.</span></span>  
  
 `functionId`  
 <span data-ttu-id="2f2f6-108">[in] Instance funkce, která se znovu kompilovaný nebo metodu označenou pro opětovnou kompilaci.</span><span class="sxs-lookup"><span data-stu-id="2f2f6-108">[in] The function instance that is being recompiled or marked for recompilation.</span></span> <span data-ttu-id="2f2f6-109">Tato hodnota může být `NULL` -li k selhání došlo na základě za metoda místo základ instance (například pokud profiler zadaný token neplatná metadata pro metodu překompilovat).</span><span class="sxs-lookup"><span data-stu-id="2f2f6-109">This value may be `NULL` if the failure occurred on a per-method basis instead of a per-instantiation basis (for example, if the profiler specified an invalid metadata token for the method to be recompiled).</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="2f2f6-110">[in] HRESULT označující podstatu tohoto selhání.</span><span class="sxs-lookup"><span data-stu-id="2f2f6-110">[in] An HRESULT that indicates the nature of the failure.</span></span> <span data-ttu-id="2f2f6-111">V části stav HRESULTS seznam hodnot.</span><span class="sxs-lookup"><span data-stu-id="2f2f6-111">See the Status HRESULTS section for a list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f2f6-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2f2f6-112">Return Value</span></span>  
 <span data-ttu-id="2f2f6-113">Návratové hodnoty v tomto zpětném volání jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="2f2f6-113">Return values from this callback are ignored.</span></span>  
  
## <a name="status-hresults"></a><span data-ttu-id="2f2f6-114">HRESULT – stav</span><span class="sxs-lookup"><span data-stu-id="2f2f6-114">Status HRESULTS</span></span>  
  
|<span data-ttu-id="2f2f6-115">Stav pole HRESULT</span><span class="sxs-lookup"><span data-stu-id="2f2f6-115">Status array HRESULT</span></span>|<span data-ttu-id="2f2f6-116">Popis</span><span class="sxs-lookup"><span data-stu-id="2f2f6-116">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="2f2f6-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2f2f6-117">E_INVALIDARG</span></span>|<span data-ttu-id="2f2f6-118">`moduleID` Nebo `methodDef` token je `NULL`.</span><span class="sxs-lookup"><span data-stu-id="2f2f6-118">The `moduleID` or `methodDef` token is `NULL`.</span></span>|  
|<span data-ttu-id="2f2f6-119">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="2f2f6-119">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="2f2f6-120">Modul dosud není zcela načteno, nebo je právě uvolňován.</span><span class="sxs-lookup"><span data-stu-id="2f2f6-120">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="2f2f6-121">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="2f2f6-121">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="2f2f6-122">Zadaný modul se generuje dynamicky (třeba podle `Reflection.Emit`) a proto není podporována touto metodou.</span><span class="sxs-lookup"><span data-stu-id="2f2f6-122">The specified module was dynamically generated (for example, by `Reflection.Emit`), and is thus not supported by this method.</span></span>|  
|<span data-ttu-id="2f2f6-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span><span class="sxs-lookup"><span data-stu-id="2f2f6-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span></span>|<span data-ttu-id="2f2f6-124">Metoda je vytvořena instance na kolekční sestavení a není tedy možné zopakovat.</span><span class="sxs-lookup"><span data-stu-id="2f2f6-124">The method is instantiated into a collectible assembly, and is therefore not able to be recompiled.</span></span> <span data-ttu-id="2f2f6-125">Všimněte si, že typy a funkce definované v kontextu jiných reflexe (například `List<MyCollectibleStruct>`) může být vytvořena na kolekční sestavení.</span><span class="sxs-lookup"><span data-stu-id="2f2f6-125">Note that types and functions defined in a non-reflection context (for example, `List<MyCollectibleStruct>`) can be instantiated into a collectible assembly.</span></span>|  
|<span data-ttu-id="2f2f6-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="2f2f6-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="2f2f6-127">Modul CLR má nedostatek paměti při pokusu označit zadanou metodu pro rekompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="2f2f6-127">The CLR ran out of memory while trying to mark the specified method for JIT recompilation.</span></span>|  
|<span data-ttu-id="2f2f6-128">Ostatní</span><span class="sxs-lookup"><span data-stu-id="2f2f6-128">Other</span></span>|<span data-ttu-id="2f2f6-129">Operační systém vrátil chybu mimo ovládací prvek CLR.</span><span class="sxs-lookup"><span data-stu-id="2f2f6-129">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="2f2f6-130">Například pokud selže volání systému ke změně ochrany přístupu k paměti stránky, se zobrazí chyba operačního systému.</span><span class="sxs-lookup"><span data-stu-id="2f2f6-130">For example, if a system call to change the access protection of a page of memory fails, the operating system error is displayed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2f2f6-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2f2f6-131">Requirements</span></span>  
 <span data-ttu-id="2f2f6-132">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f2f6-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f2f6-133">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2f2f6-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2f2f6-134">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f2f6-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f2f6-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f2f6-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f2f6-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f2f6-136">See also</span></span>

- [<span data-ttu-id="2f2f6-137">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f2f6-137">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="2f2f6-138">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f2f6-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
