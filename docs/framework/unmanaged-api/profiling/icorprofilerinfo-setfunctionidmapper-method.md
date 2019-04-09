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
ms.openlocfilehash: 6cbbe85a99d0c78bd3d95ee654bdc13e376d017d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125221"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a><span data-ttu-id="51e28-102">ICorProfilerInfo::SetFunctionIDMapper – metoda</span><span class="sxs-lookup"><span data-stu-id="51e28-102">ICorProfilerInfo::SetFunctionIDMapper Method</span></span>
<span data-ttu-id="51e28-103">Určuje funkci, která bude volána k mapování profiler implementovat `FunctionID` hodnoty pro alternativní hodnoty, které jsou předány do profileru funkce zachytávání vstupu/výstupu.</span><span class="sxs-lookup"><span data-stu-id="51e28-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51e28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51e28-104">Syntax</span></span>  
  
```  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51e28-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="51e28-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="51e28-106">[in] Ukazatel [functionidmapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) implementace, která bude volána k mapování `FunctionID` hodnoty na alternativní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="51e28-106">[in] A pointer to the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51e28-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="51e28-107">Remarks</span></span>  
 <span data-ttu-id="51e28-108">Alternativy k `FunctionID` hodnoty budou předána pracovnímu zachytávání vstupu/výstupu profileru – funkce ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), a [functiontailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)) které jsou určeny [ICorProfilerInfo2::setenterleavefunctionhooks2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="51e28-108">The alternatives for the `FunctionID` values will be passed to the profiler's function entry/exit hooks ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)) that are specified by the [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) method.</span></span>  
  
 <span data-ttu-id="51e28-109">`FunctionIDMapper` Lze nastavit pouze jednou a doporučuje se, že jste nastavili v [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="51e28-109">The `FunctionIDMapper` can be set only once and it is recommended that you set it in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51e28-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="51e28-110">Requirements</span></span>  
 <span data-ttu-id="51e28-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51e28-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51e28-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="51e28-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="51e28-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51e28-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="51e28-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="51e28-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="51e28-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51e28-115">See also</span></span>

- [<span data-ttu-id="51e28-116">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="51e28-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
