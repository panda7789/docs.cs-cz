---
title: ICorProfilerCallback::JITCachedFunctionSearchFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type:
- apiref
ms.openlocfilehash: ad155c4efb9f11565eeed8bc0a3540311aca4eb7
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866270"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="099b0-102">ICorProfilerCallback::JITCachedFunctionSearchFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="099b0-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>
<span data-ttu-id="099b0-103">Upozorní profileru, že vyhledávání skončilo pro funkci, která byla dříve kompilována pomocí generátoru nativních imagí (NGen. exe).</span><span class="sxs-lookup"><span data-stu-id="099b0-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="099b0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="099b0-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a><span data-ttu-id="099b0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="099b0-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="099b0-106">\[in] ID funkce, pro kterou bylo hledání provedeno.</span><span class="sxs-lookup"><span data-stu-id="099b0-106">\[in] The ID of the function for which the search was performed.</span></span>

- `result`

  <span data-ttu-id="099b0-107">\[in] hodnota výčtu [COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md) , která určuje výsledek hledání.</span><span class="sxs-lookup"><span data-stu-id="099b0-107">\[in] A value of the [COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>

## <a name="remarks"></a><span data-ttu-id="099b0-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="099b0-108">Remarks</span></span>  
 <span data-ttu-id="099b0-109">V .NET Framework verze 2,0 nebudou zpětná volání [ICorProfilerCallback:: jitcachedfunctionsearchstarted –](icorprofilercallback-jitcachedfunctionsearchstarted-method.md) a `JITCachedFunctionSearchFinished` pro všechny funkce v normálních bitových kopiích Ngen provedeny.</span><span class="sxs-lookup"><span data-stu-id="099b0-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="099b0-110">Zpětná volání pro všechny funkce v imagi budou generovat pouze image NGen optimalizované pro Profiler.</span><span class="sxs-lookup"><span data-stu-id="099b0-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="099b0-111">V důsledku dodatečné režie by měl Profiler vyžádat image NGen optimalizované profilerem jenom v případě, že má v úmyslu použít tato zpětná volání k vynucení funkce JIT just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="099b0-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="099b0-112">V opačném případě by Profiler měl používat opožděnou strategii pro shromažďování informací o funkcích.</span><span class="sxs-lookup"><span data-stu-id="099b0-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="099b0-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="099b0-113">Requirements</span></span>  
 <span data-ttu-id="099b0-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="099b0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="099b0-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="099b0-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="099b0-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="099b0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="099b0-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="099b0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="099b0-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="099b0-118">See also</span></span>

- [<span data-ttu-id="099b0-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="099b0-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
