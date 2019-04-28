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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b0e78e10f092bce1c8f7762362f02b7a403c86a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597233"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="c9552-102">ICorProfilerCallback::JITCachedFunctionSearchFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="c9552-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>
<span data-ttu-id="c9552-103">Upozornění profileru dokončení vyhledávání pro funkci, která se zkompilovala pomocí dříve Native Image Generator (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="c9552-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9552-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9552-104">Syntax</span></span>  
  
```  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9552-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9552-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="c9552-106">[in] ID funkce, pro který bylo hledání provedeno.</span><span class="sxs-lookup"><span data-stu-id="c9552-106">[in] The ID of the function for which the search was performed.</span></span>  
  
 `result`  
 <span data-ttu-id="c9552-107">[in] Hodnota [cor_prf_jit_cache –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) výčet, který určuje výsledek hledání.</span><span class="sxs-lookup"><span data-stu-id="c9552-107">[in] A value of the [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9552-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c9552-108">Remarks</span></span>  
 <span data-ttu-id="c9552-109">V rozhraní .NET Framework verze 2.0 [icorprofilercallback::jitcachedfunctionsearchstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) a `JITCachedFunctionSearchFinished` zpětná volání, nebude možné zavést pro všechny funkce v běžných bitových kopií technologie NGen.</span><span class="sxs-lookup"><span data-stu-id="c9552-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="c9552-110">Pouze obrázků NGen optimalizovaná pro profiler vygeneruje zpětná volání pro všechny funkce v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="c9552-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="c9552-111">Ale z důvodu další režie profileru by měl požádat o profileru optimalizované Image NGen pouze v případě, že to chce využít tato zpětná volání k vynucení funkce kompilované just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="c9552-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="c9552-112">Profiler by jinak použijte opožděné strategie pro shromažďování informací funkce.</span><span class="sxs-lookup"><span data-stu-id="c9552-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9552-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9552-113">Requirements</span></span>  
 <span data-ttu-id="c9552-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9552-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9552-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c9552-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c9552-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9552-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9552-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9552-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9552-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9552-118">See also</span></span>

- [<span data-ttu-id="c9552-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9552-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
