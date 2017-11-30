---
title: "ICorProfilerCallback::FunctionUnloadStarted – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.FunctionUnloadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: efd08eedf6812a46a46135eaa6f0089257f0a209
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="7942b-102">ICorProfilerCallback::FunctionUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="7942b-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="7942b-103">Upozorní profileru, že modul runtime bylo zahájeno Unload funkce.</span><span class="sxs-lookup"><span data-stu-id="7942b-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7942b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7942b-104">Syntax</span></span>  
  
```  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="7942b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7942b-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="7942b-106">[v] ID funkce, která odpojení.</span><span class="sxs-lookup"><span data-stu-id="7942b-106">[in] The ID of the function that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7942b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7942b-107">Remarks</span></span>  
 <span data-ttu-id="7942b-108">Hodnota `functionId` parametr je platný už po návratu tato metoda volajícímu.</span><span class="sxs-lookup"><span data-stu-id="7942b-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7942b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7942b-109">Requirements</span></span>  
 <span data-ttu-id="7942b-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7942b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7942b-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7942b-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7942b-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7942b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7942b-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7942b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7942b-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="7942b-114">See Also</span></span>  
 [<span data-ttu-id="7942b-115">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7942b-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
