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
ms.openlocfilehash: 52ab9a089b5def4f3db2f99abc5a718d66cca739
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863449"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a><span data-ttu-id="35523-102">ICorProfilerInfo::SetFunctionIDMapper – metoda</span><span class="sxs-lookup"><span data-stu-id="35523-102">ICorProfilerInfo::SetFunctionIDMapper Method</span></span>
<span data-ttu-id="35523-103">Určuje funkci implementovanou profilerem, která bude volána k namapování `FunctionID` hodnot na alternativní hodnoty, které jsou předány do vstupních a ukončovacích funkcí profileru.</span><span class="sxs-lookup"><span data-stu-id="35523-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35523-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35523-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35523-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="35523-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="35523-106">pro Ukazatel na implementaci [FunctionIDMapper –](functionidmapper-function.md) , která bude volána pro mapování `FunctionID`ch hodnot na jejich alternativní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="35523-106">[in] A pointer to the [FunctionIDMapper](functionidmapper-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35523-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="35523-107">Remarks</span></span>  
 <span data-ttu-id="35523-108">Alternativy `FunctionID`ch hodnot budou předány příjezdce a ukončení funkce profileru ([FunctionEnter2](functionenter2-function.md), [FunctionLeave2 –](functionleave2-function.md)a [FunctionTailcall2 –](functiontailcall2-function.md)), které jsou určeny metodou [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2 –](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="35523-108">The alternatives for the `FunctionID` values will be passed to the profiler's function entry/exit hooks ([FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md)) that are specified by the [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) method.</span></span>  
  
 <span data-ttu-id="35523-109">`FunctionIDMapper` lze nastavit pouze jednou a je doporučeno ji nastavit ve zpětném volání [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="35523-109">The `FunctionIDMapper` can be set only once and it is recommended that you set it in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35523-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="35523-110">Requirements</span></span>  
 <span data-ttu-id="35523-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35523-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35523-112">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="35523-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="35523-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="35523-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35523-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35523-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35523-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="35523-115">See also</span></span>

- [<span data-ttu-id="35523-116">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="35523-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
