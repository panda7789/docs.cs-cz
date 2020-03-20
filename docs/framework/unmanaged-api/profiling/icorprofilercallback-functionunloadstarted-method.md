---
title: ICorProfilerCallback::FunctionUnloadStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.FunctionUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type:
- apiref
ms.openlocfilehash: 988843559e55cc4cacd2a40bb3e6ac51721e99b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175158"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="9c757-102">ICorProfilerCallback::FunctionUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="9c757-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="9c757-103">Upozorní profiler, že runtime začal uvolnit funkci.</span><span class="sxs-lookup"><span data-stu-id="9c757-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c757-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c757-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);
```  
  
## <a name="parameters"></a><span data-ttu-id="9c757-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c757-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="9c757-106">\[in] ID funkce, která je uvolněna.</span><span class="sxs-lookup"><span data-stu-id="9c757-106">\[in] The ID of the function that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="9c757-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9c757-107">Remarks</span></span>  
 <span data-ttu-id="9c757-108">Hodnota parametru `functionId` již není platná poté, co se tato metoda vrátí volajícímu.</span><span class="sxs-lookup"><span data-stu-id="9c757-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c757-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9c757-109">Requirements</span></span>  
 <span data-ttu-id="9c757-110">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c757-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c757-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9c757-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9c757-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c757-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c757-113">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c757-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c757-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c757-114">See also</span></span>

- [<span data-ttu-id="9c757-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c757-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
