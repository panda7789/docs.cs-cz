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
ms.openlocfilehash: 2b228337a55d50b94da966b45877e2000b3c03e4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866309"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="eda66-102">ICorProfilerCallback::FunctionUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="eda66-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="eda66-103">Upozorní profileru, že modul runtime zahájil uvolnění funkce.</span><span class="sxs-lookup"><span data-stu-id="eda66-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eda66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eda66-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="eda66-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eda66-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="eda66-106">\[v] ID funkce, která se právě načítá.</span><span class="sxs-lookup"><span data-stu-id="eda66-106">\[in] The ID of the function that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="eda66-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eda66-107">Remarks</span></span>  
 <span data-ttu-id="eda66-108">Hodnota parametru `functionId` již není platná poté, co se tato metoda vrátí volajícímu.</span><span class="sxs-lookup"><span data-stu-id="eda66-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eda66-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eda66-109">Requirements</span></span>  
 <span data-ttu-id="eda66-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eda66-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eda66-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="eda66-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eda66-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="eda66-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eda66-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eda66-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eda66-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eda66-114">See also</span></span>

- [<span data-ttu-id="eda66-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eda66-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
