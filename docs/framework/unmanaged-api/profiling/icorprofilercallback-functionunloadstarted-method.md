---
title: "ICorProfilerCallback::FunctionUnloadStarted – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 957b5a89dbb3e780b0e5512afe405e669fdbecce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="243bc-102">ICorProfilerCallback::FunctionUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="243bc-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="243bc-103">Upozorní profileru, že modul runtime bylo zahájeno Unload funkce.</span><span class="sxs-lookup"><span data-stu-id="243bc-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="243bc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="243bc-104">Syntax</span></span>  
  
```  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="243bc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="243bc-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="243bc-106">[v] ID funkce, která odpojení.</span><span class="sxs-lookup"><span data-stu-id="243bc-106">[in] The ID of the function that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="243bc-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="243bc-107">Remarks</span></span>  
 <span data-ttu-id="243bc-108">Hodnota `functionId` parametr je platný už po návratu tato metoda volajícímu.</span><span class="sxs-lookup"><span data-stu-id="243bc-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="243bc-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="243bc-109">Requirements</span></span>  
 <span data-ttu-id="243bc-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="243bc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="243bc-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="243bc-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="243bc-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="243bc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="243bc-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="243bc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="243bc-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="243bc-114">See Also</span></span>  
 [<span data-ttu-id="243bc-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="243bc-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
