---
title: "ICorProfilerInfo::SetFunctionIDMapper – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.SetFunctionIDMapper
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::SetFunctionIDMapper
helpviewer_keywords:
- ICorProfilerInfo::SetFunctionIDMapper method [.NET Framework profiling]
- SetFunctionIDMapper method [.NET Framework profiling]
ms.assetid: 1a6e5dae-d366-4497-9c02-7b5b1f43f9ec
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 11f89b8d6697a2abf5a2787f0f4f10436e0a0212
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a><span data-ttu-id="25d1f-102">ICorProfilerInfo::SetFunctionIDMapper – metoda</span><span class="sxs-lookup"><span data-stu-id="25d1f-102">ICorProfilerInfo::SetFunctionIDMapper Method</span></span>
<span data-ttu-id="25d1f-103">Určuje implementované profileru funkci, která bude volána k mapování `FunctionID` hodnoty pro alternativní hodnoty, které jsou předávány profileru funkce háky přechodu.</span><span class="sxs-lookup"><span data-stu-id="25d1f-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25d1f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25d1f-104">Syntax</span></span>  
  
```  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25d1f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25d1f-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="25d1f-106">[v] Ukazatel [functionidmapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) implementace, která bude volána k mapování `FunctionID` hodnoty na alternativní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="25d1f-106">[in] A pointer to the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25d1f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25d1f-107">Remarks</span></span>  
 <span data-ttu-id="25d1f-108">Alternativy pro `FunctionID` hodnoty se předá háky přechodu profileru – funkce ([functionenter2 –](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [functionleave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), a [functiontailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)) které jsou určené [ICorProfilerInfo2::setenterleavefunctionhooks2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="25d1f-108">The alternatives for the `FunctionID` values will be passed to the profiler's function entry/exit hooks ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)) that are specified by the [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) method.</span></span>  
  
 <span data-ttu-id="25d1f-109">`FunctionIDMapper` Lze nastavit pouze jednou a se doporučuje nastavit [icorprofilercallback::Initialize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="25d1f-109">The `FunctionIDMapper` can be set only once and it is recommended that you set it in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25d1f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25d1f-110">Requirements</span></span>  
 <span data-ttu-id="25d1f-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25d1f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25d1f-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="25d1f-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="25d1f-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25d1f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25d1f-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25d1f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25d1f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="25d1f-115">See Also</span></span>  
 [<span data-ttu-id="25d1f-116">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25d1f-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
