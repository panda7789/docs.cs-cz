---
title: ICorProfilerInfo3::SetFunctionIDMapper2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetFunctionIDMapper2 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetFunctionIDMapper2
helpviewer_keywords:
- SetFunctionIDMapper2 method [.NET Framework profiling]
- ICorProfilerInfo3::SetFunctionIDMapper2 method [.NET Framework profiling]
ms.assetid: 8cdb1188-952a-4ba8-9f05-bfebc18cdd29
topic_type:
- apiref
ms.openlocfilehash: 723cb277a7df592e0494505018f7422e4e40f5f6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496149"
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a><span data-ttu-id="1aaa8-102">ICorProfilerInfo3::SetFunctionIDMapper2 – metoda</span><span class="sxs-lookup"><span data-stu-id="1aaa8-102">ICorProfilerInfo3::SetFunctionIDMapper2 Method</span></span>
<span data-ttu-id="1aaa8-103">Určuje funkci implementovanou v profileru, která bude volána k mapování `FunctionID` hodnot na alternativní hodnoty, které jsou předány do vstupních a ukončovacích funkcí profileru.</span><span class="sxs-lookup"><span data-stu-id="1aaa8-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span> <span data-ttu-id="1aaa8-104">Tato metoda rozšiřuje metodu [ICorProfilerInfo:: SetFunctionIDMapper –](icorprofilerinfo-setfunctionidmapper-method.md) s parametrem další dat, který profilery mohou použít k jednoznačnému rozlišení mezi moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="1aaa8-104">This method extends the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method with an additional data parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1aaa8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1aaa8-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1aaa8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1aaa8-106">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="1aaa8-107">pro Ukazatel na implementaci [FunctionIDMapper2 –](functionidmapper2-function.md) , která bude volána pro mapování `FunctionID` hodnot na jejich alternativní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1aaa8-107">[in] A pointer to a [FunctionIDMapper2](functionidmapper2-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
 `clientData`  
 <span data-ttu-id="1aaa8-108">pro Ukazatel, který je předán všem voláním funkce [FunctionIDMapper2 –](functionidmapper2-function.md) provedeným aktuálním modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="1aaa8-108">[in] A pointer that is passed to every [FunctionIDMapper2](functionidmapper2-function.md) function call made by the current runtime.</span></span> <span data-ttu-id="1aaa8-109">Profiler může tyto informace použít k jednoznačnému rozlišení mezi moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="1aaa8-109">The profiler can use this information to disambiguate among runtimes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1aaa8-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1aaa8-110">Return Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1aaa8-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1aaa8-111">Remarks</span></span>  
 <span data-ttu-id="1aaa8-112">Alternativy hodnot FunctionID budou předány příjezdce a ukončení funkce profileru ([FunctionEnter3 –](functionenter3-function.md), [FunctionLeave3 –](functionleave3-function.md)a [FunctionTailcall3 –](functiontailcall3-function.md); nebo [FunctionEnter3WithInfo –](functionenter3withinfo-function.md), [Functionleave3withinfo –](functionleave3withinfo-function.md)a [FunctionTailcall3WithInfo –](functiontailcall3withinfo-function.md)), které jsou určeny metodou [SetEnterLeaveFunctionHooks3 –](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) nebo [SetEnterLeaveFunctionHooks3WithInfo –](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1aaa8-112">The alternatives for the FunctionID values will be passed to the profiler's function entry/exit hooks ([FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md); or [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)) that are specified by the [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) or [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method.</span></span>  
  
 <span data-ttu-id="1aaa8-113">`FunctionIDMapper2`Metodu lze nastavit pouze jednou. doporučujeme ji nastavit ve zpětném volání [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1aaa8-113">The `FunctionIDMapper2` method can be set only once; we recommend that you set it in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1aaa8-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1aaa8-114">Requirements</span></span>  
 <span data-ttu-id="1aaa8-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1aaa8-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1aaa8-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1aaa8-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1aaa8-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1aaa8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1aaa8-118">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1aaa8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aaa8-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1aaa8-119">See also</span></span>

- [<span data-ttu-id="1aaa8-120">SetFunctionIDMapper –</span><span class="sxs-lookup"><span data-stu-id="1aaa8-120">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="1aaa8-121">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1aaa8-121">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="1aaa8-122">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="1aaa8-122">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="1aaa8-123">Profilace</span><span class="sxs-lookup"><span data-stu-id="1aaa8-123">Profiling</span></span>](index.md)
