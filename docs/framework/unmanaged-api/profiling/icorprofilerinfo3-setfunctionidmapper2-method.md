---
title: "ICorProfilerInfo3::SetFunctionIDMapper2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.SetFunctionIDMapper2 Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::SetFunctionIDMapper2
helpviewer_keywords:
- SetFunctionIDMapper2 method [.NET Framework profiling]
- ICorProfilerInfo3::SetFunctionIDMapper2 method [.NET Framework profiling]
ms.assetid: 8cdb1188-952a-4ba8-9f05-bfebc18cdd29
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: adc23b8774737f9884ded7ec1e3a891ed8b63b2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a><span data-ttu-id="75eb6-102">ICorProfilerInfo3::SetFunctionIDMapper2 – metoda</span><span class="sxs-lookup"><span data-stu-id="75eb6-102">ICorProfilerInfo3::SetFunctionIDMapper2 Method</span></span>
<span data-ttu-id="75eb6-103">Určuje implementované profileru funkci, která bude volána k mapování `FunctionID` hodnoty pro alternativní hodnoty, které jsou předávány profileru funkce háky přechodu.</span><span class="sxs-lookup"><span data-stu-id="75eb6-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span> <span data-ttu-id="75eb6-104">Tato metoda rozšiřuje [icorprofilerinfo::setfunctionidmapper –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) metoda s parametrem další data, která profilery může použít k rozlišení mezi moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="75eb6-104">This method extends the [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) method with an additional data parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75eb6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75eb6-105">Syntax</span></span>  
  
```  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="75eb6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="75eb6-106">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="75eb6-107">[v] Ukazatel [functionidmapper2 –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) implementace, která bude volána k mapování `FunctionID` hodnoty na alternativní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="75eb6-107">[in] A pointer to a [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
 `clientData`  
 <span data-ttu-id="75eb6-108">[v] Ukazatele, který je předán do každé [functionidmapper2 –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) provedené aktuálního běhového modulu volání funkce.</span><span class="sxs-lookup"><span data-stu-id="75eb6-108">[in] A pointer that is passed to every [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) function call made by the current runtime.</span></span> <span data-ttu-id="75eb6-109">Profileru můžete tyto informace slouží k rozlišení mezi moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="75eb6-109">The profiler can use this information to disambiguate among runtimes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75eb6-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="75eb6-110">Return Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75eb6-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="75eb6-111">Remarks</span></span>  
 <span data-ttu-id="75eb6-112">Alternativy pro hodnoty FunctionID se předá háky přechodu profileru – funkce ([functionenter3 –](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [functionleave3 –](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), a [functiontailcall3 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) ; nebo [functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), a [functiontailcall3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)), jsou určené [ Setenterleavefunctionhooks3 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) nebo [setenterleavefunctionhooks3withinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="75eb6-112">The alternatives for the FunctionID values will be passed to the profiler's function entry/exit hooks ([FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md); or [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)) that are specified by the [SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) or [SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method.</span></span>  
  
 <span data-ttu-id="75eb6-113">`FunctionIDMapper2` Metoda lze nastavit pouze jednou; doporučujeme nastavit [icorprofilercallback::Initialize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="75eb6-113">The `FunctionIDMapper2` method can be set only once; we recommend that you set it in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75eb6-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="75eb6-114">Requirements</span></span>  
 <span data-ttu-id="75eb6-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75eb6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75eb6-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="75eb6-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="75eb6-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75eb6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75eb6-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75eb6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75eb6-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="75eb6-119">See Also</span></span>  
 [<span data-ttu-id="75eb6-120">Setfunctionidmapper –</span><span class="sxs-lookup"><span data-stu-id="75eb6-120">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="75eb6-121">Icorprofilerinfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="75eb6-121">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="75eb6-122">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="75eb6-122">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="75eb6-123">Profilace</span><span class="sxs-lookup"><span data-stu-id="75eb6-123">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
