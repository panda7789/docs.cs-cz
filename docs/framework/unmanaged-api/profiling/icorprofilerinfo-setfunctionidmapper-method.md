---
title: ICorProfilerInfo::SetFunctionIDMapper – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetFunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetFunctionIDMapper
helpviewer_keywords:
- ICorProfilerInfo::SetFunctionIDMapper method [.NET Framework profiling]
- SetFunctionIDMapper method [.NET Framework profiling]
ms.assetid: 1a6e5dae-d366-4497-9c02-7b5b1f43f9ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3e5d9c9596d0bb5e61bd7aed4caaa986759cfa54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455728"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a><span data-ttu-id="f779b-102">ICorProfilerInfo::SetFunctionIDMapper – metoda</span><span class="sxs-lookup"><span data-stu-id="f779b-102">ICorProfilerInfo::SetFunctionIDMapper Method</span></span>
<span data-ttu-id="f779b-103">Určuje implementované profileru funkci, která bude volána k mapování `FunctionID` hodnoty pro alternativní hodnoty, které jsou předávány profileru funkce háky přechodu.</span><span class="sxs-lookup"><span data-stu-id="f779b-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f779b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f779b-104">Syntax</span></span>  
  
```  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f779b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f779b-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="f779b-106">[v] Ukazatel [functionidmapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) implementace, která bude volána k mapování `FunctionID` hodnoty na alternativní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f779b-106">[in] A pointer to the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f779b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f779b-107">Remarks</span></span>  
 <span data-ttu-id="f779b-108">Alternativy pro `FunctionID` hodnoty se předá háky přechodu profileru – funkce ([functionenter2 –](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [functionleave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), a [functiontailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)) které jsou určené [ICorProfilerInfo2::setenterleavefunctionhooks2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="f779b-108">The alternatives for the `FunctionID` values will be passed to the profiler's function entry/exit hooks ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)) that are specified by the [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) method.</span></span>  
  
 <span data-ttu-id="f779b-109">`FunctionIDMapper` Lze nastavit pouze jednou a se doporučuje nastavit [icorprofilercallback::Initialize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="f779b-109">The `FunctionIDMapper` can be set only once and it is recommended that you set it in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f779b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f779b-110">Requirements</span></span>  
 <span data-ttu-id="f779b-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f779b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f779b-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f779b-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f779b-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f779b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f779b-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f779b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f779b-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f779b-115">See Also</span></span>  
 [<span data-ttu-id="f779b-116">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f779b-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
