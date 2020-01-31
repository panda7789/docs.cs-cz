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
ms.openlocfilehash: 107f596801832809e64088c85540c441e66189cf
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868470"
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a><span data-ttu-id="d21a0-102">ICorProfilerInfo3::SetFunctionIDMapper2 – metoda</span><span class="sxs-lookup"><span data-stu-id="d21a0-102">ICorProfilerInfo3::SetFunctionIDMapper2 Method</span></span>
<span data-ttu-id="d21a0-103">Určuje funkci implementovanou profilerem, která bude volána k namapování `FunctionID` hodnot na alternativní hodnoty, které jsou předány do vstupních a ukončovacích funkcí profileru.</span><span class="sxs-lookup"><span data-stu-id="d21a0-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span> <span data-ttu-id="d21a0-104">Tato metoda rozšiřuje metodu [ICorProfilerInfo:: SetFunctionIDMapper –](icorprofilerinfo-setfunctionidmapper-method.md) s parametrem další dat, který profilery mohou použít k jednoznačnému rozlišení mezi moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="d21a0-104">This method extends the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method with an additional data parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d21a0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d21a0-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d21a0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d21a0-106">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="d21a0-107">pro Ukazatel na implementaci [FunctionIDMapper2 –](functionidmapper2-function.md) , která bude volána pro mapování `FunctionID`ch hodnot na jejich alternativní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d21a0-107">[in] A pointer to a [FunctionIDMapper2](functionidmapper2-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
 `clientData`  
 <span data-ttu-id="d21a0-108">pro Ukazatel, který je předán všem voláním funkce [FunctionIDMapper2 –](functionidmapper2-function.md) provedeným aktuálním modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="d21a0-108">[in] A pointer that is passed to every [FunctionIDMapper2](functionidmapper2-function.md) function call made by the current runtime.</span></span> <span data-ttu-id="d21a0-109">Profiler může tyto informace použít k jednoznačnému rozlišení mezi moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="d21a0-109">The profiler can use this information to disambiguate among runtimes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d21a0-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d21a0-110">Return Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d21a0-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d21a0-111">Remarks</span></span>  
 <span data-ttu-id="d21a0-112">Alternativy hodnot FunctionID budou předány příjezdce a ukončení funkce profileru ([FunctionEnter3 –](functionenter3-function.md), [FunctionLeave3 –](functionleave3-function.md)a [FunctionTailcall3 –](functiontailcall3-function.md); nebo [FunctionEnter3WithInfo –](functionenter3withinfo-function.md), [Functionleave3withinfo –](functionleave3withinfo-function.md)a [FunctionTailcall3WithInfo –](functiontailcall3withinfo-function.md)), které jsou určeny metodou [SetEnterLeaveFunctionHooks3 –](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) nebo [SetEnterLeaveFunctionHooks3WithInfo –](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d21a0-112">The alternatives for the FunctionID values will be passed to the profiler's function entry/exit hooks ([FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md); or [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)) that are specified by the [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) or [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method.</span></span>  
  
 <span data-ttu-id="d21a0-113">Metodu `FunctionIDMapper2` lze nastavit pouze jednou. Doporučujeme, abyste ji nastavili ve zpětném volání [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d21a0-113">The `FunctionIDMapper2` method can be set only once; we recommend that you set it in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d21a0-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d21a0-114">Requirements</span></span>  
 <span data-ttu-id="d21a0-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d21a0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d21a0-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d21a0-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d21a0-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d21a0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d21a0-118">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d21a0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d21a0-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d21a0-119">See also</span></span>

- [<span data-ttu-id="d21a0-120">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="d21a0-120">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="d21a0-121">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d21a0-121">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="d21a0-122">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d21a0-122">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="d21a0-123">Profilace</span><span class="sxs-lookup"><span data-stu-id="d21a0-123">Profiling</span></span>](index.md)
