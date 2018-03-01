---
title: "ICorProfilerInfo3::SetFunctionIDMapper2 – metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0a58b01345fe1acb7434b8896ebbc8548ab68a98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a><span data-ttu-id="6a6ba-102">ICorProfilerInfo3::SetFunctionIDMapper2 – metoda</span><span class="sxs-lookup"><span data-stu-id="6a6ba-102">ICorProfilerInfo3::SetFunctionIDMapper2 Method</span></span>
<span data-ttu-id="6a6ba-103">Určuje implementované profileru funkci, která bude volána k mapování `FunctionID` hodnoty pro alternativní hodnoty, které jsou předávány profileru funkce háky přechodu.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span> <span data-ttu-id="6a6ba-104">Tato metoda rozšiřuje [icorprofilerinfo::setfunctionidmapper –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) metoda s parametrem další data, která profilery může použít k rozlišení mezi moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-104">This method extends the [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) method with an additional data parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a6ba-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a6ba-105">Syntax</span></span>  
  
```  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a6ba-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a6ba-106">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="6a6ba-107">[v] Ukazatel [functionidmapper2 –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) implementace, která bude volána k mapování `FunctionID` hodnoty na alternativní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-107">[in] A pointer to a [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
 `clientData`  
 <span data-ttu-id="6a6ba-108">[v] Ukazatele, který je předán do každé [functionidmapper2 –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) provedené aktuálního běhového modulu volání funkce.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-108">[in] A pointer that is passed to every [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) function call made by the current runtime.</span></span> <span data-ttu-id="6a6ba-109">Profileru můžete tyto informace slouží k rozlišení mezi moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-109">The profiler can use this information to disambiguate among runtimes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a6ba-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6a6ba-110">Return Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a6ba-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a6ba-111">Remarks</span></span>  
 <span data-ttu-id="6a6ba-112">Alternativy pro hodnoty FunctionID se předá háky přechodu profileru – funkce ([functionenter3 –](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [functionleave3 –](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), a [functiontailcall3 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) ; nebo [functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), a [functiontailcall3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)), jsou určené [ Setenterleavefunctionhooks3 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) nebo [setenterleavefunctionhooks3withinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-112">The alternatives for the FunctionID values will be passed to the profiler's function entry/exit hooks ([FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md); or [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)) that are specified by the [SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) or [SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method.</span></span>  
  
 <span data-ttu-id="6a6ba-113">`FunctionIDMapper2` Metoda lze nastavit pouze jednou; doporučujeme nastavit [icorprofilercallback::Initialize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-113">The `FunctionIDMapper2` method can be set only once; we recommend that you set it in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a6ba-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a6ba-114">Requirements</span></span>  
 <span data-ttu-id="6a6ba-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a6ba-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a6ba-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6a6ba-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6a6ba-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a6ba-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a6ba-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a6ba-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a6ba-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a6ba-119">See Also</span></span>  
 [<span data-ttu-id="6a6ba-120">Setfunctionidmapper –</span><span class="sxs-lookup"><span data-stu-id="6a6ba-120">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="6a6ba-121">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a6ba-121">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="6a6ba-122">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="6a6ba-122">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="6a6ba-123">Profilace</span><span class="sxs-lookup"><span data-stu-id="6a6ba-123">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
