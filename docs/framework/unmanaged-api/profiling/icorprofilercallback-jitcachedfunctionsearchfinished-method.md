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
ms.openlocfilehash: 89c7b0fe0f3ade3f57aa50b100bc9b4ecc904a17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451994"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="6cb0b-102">ICorProfilerCallback::JITCachedFunctionSearchFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="6cb0b-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>
<span data-ttu-id="6cb0b-103">Upozorní profileru, že bylo dokončeno vyhledávání pro funkce, který byl kompilován s použitím dříve generátor (NGen.exe).</span><span class="sxs-lookup"><span data-stu-id="6cb0b-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cb0b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cb0b-104">Syntax</span></span>  
  
```  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6cb0b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6cb0b-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="6cb0b-106">[v] ID funkce, pro které se provádí vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-106">[in] The ID of the function for which the search was performed.</span></span>  
  
 `result`  
 <span data-ttu-id="6cb0b-107">[v] Hodnota [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) výčet, který určuje výsledek hledání.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-107">[in] A value of the [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cb0b-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6cb0b-108">Remarks</span></span>  
 <span data-ttu-id="6cb0b-109">V rozhraní .NET Framework verze 2.0 [icorprofilercallback::jitcachedfunctionsearchstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) a `JITCachedFunctionSearchFinished` zpětná volání nebude možné vytvořit pro všechny funkce v pravidelných NGen bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="6cb0b-110">Pouze NGen obrázky optimalizované pro profileru vygeneruje zpětných volání pro všechny funkce v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="6cb0b-111">Však z důvodu další režie profileru měli požádat o optimalizované profileru obrazy NGen pouze v případě, že má v úmyslu použít tyto zpětná volání, které vynutí funkce, která má být kompilované v běhu (JIT).</span><span class="sxs-lookup"><span data-stu-id="6cb0b-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="6cb0b-112">Profileru, jinak hodnota by měla použít opožděné strategie pro shromažďování informací funkce.</span><span class="sxs-lookup"><span data-stu-id="6cb0b-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cb0b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6cb0b-113">Requirements</span></span>  
 <span data-ttu-id="6cb0b-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cb0b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cb0b-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6cb0b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6cb0b-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6cb0b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6cb0b-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cb0b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cb0b-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="6cb0b-118">See Also</span></span>  
 [<span data-ttu-id="6cb0b-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6cb0b-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
