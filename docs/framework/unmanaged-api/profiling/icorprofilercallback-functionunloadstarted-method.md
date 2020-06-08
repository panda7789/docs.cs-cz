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
ms.openlocfilehash: 320aaf074452fd02cd8ee8e80194a4c35b831eb4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503377"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="42269-102">ICorProfilerCallback::FunctionUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="42269-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="42269-103">Upozorní profileru, že modul runtime zahájil uvolnění funkce.</span><span class="sxs-lookup"><span data-stu-id="42269-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42269-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42269-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);
```  
  
## <a name="parameters"></a><span data-ttu-id="42269-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42269-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="42269-106">\[v] ID funkce, která je uvolněna.</span><span class="sxs-lookup"><span data-stu-id="42269-106">\[in] The ID of the function that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="42269-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="42269-107">Remarks</span></span>  
 <span data-ttu-id="42269-108">Hodnota `functionId` parametru již není platná poté, co se tato metoda vrátí volajícímu.</span><span class="sxs-lookup"><span data-stu-id="42269-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42269-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42269-109">Requirements</span></span>  
 <span data-ttu-id="42269-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42269-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42269-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="42269-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="42269-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="42269-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42269-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42269-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42269-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42269-114">See also</span></span>

- [<span data-ttu-id="42269-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42269-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
