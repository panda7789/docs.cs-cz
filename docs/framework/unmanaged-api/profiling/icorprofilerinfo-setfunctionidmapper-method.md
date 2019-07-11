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
ms.openlocfilehash: c4eefbb100b215cf4ac98352f37488b21cde49d8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772146"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a><span data-ttu-id="a008a-102">ICorProfilerInfo::SetFunctionIDMapper – metoda</span><span class="sxs-lookup"><span data-stu-id="a008a-102">ICorProfilerInfo::SetFunctionIDMapper Method</span></span>
<span data-ttu-id="a008a-103">Určuje funkci, která bude volána k mapování profiler implementovat `FunctionID` hodnoty pro alternativní hodnoty, které jsou předány do profileru funkce zachytávání vstupu/výstupu.</span><span class="sxs-lookup"><span data-stu-id="a008a-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a008a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a008a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a008a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a008a-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="a008a-106">[in] Ukazatel [functionidmapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) implementace, která bude volána k mapování `FunctionID` hodnoty na alternativní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a008a-106">[in] A pointer to the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a008a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a008a-107">Remarks</span></span>  
 <span data-ttu-id="a008a-108">Alternativy k `FunctionID` hodnoty budou předána pracovnímu zachytávání vstupu/výstupu profileru – funkce ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), a [functiontailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)) které jsou určeny [ICorProfilerInfo2::setenterleavefunctionhooks2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a008a-108">The alternatives for the `FunctionID` values will be passed to the profiler's function entry/exit hooks ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)) that are specified by the [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) method.</span></span>  
  
 <span data-ttu-id="a008a-109">`FunctionIDMapper` Lze nastavit pouze jednou a doporučuje se, že jste nastavili v [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="a008a-109">The `FunctionIDMapper` can be set only once and it is recommended that you set it in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a008a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a008a-110">Requirements</span></span>  
 <span data-ttu-id="a008a-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a008a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a008a-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a008a-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a008a-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a008a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a008a-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a008a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a008a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a008a-115">See also</span></span>

- [<span data-ttu-id="a008a-116">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a008a-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
