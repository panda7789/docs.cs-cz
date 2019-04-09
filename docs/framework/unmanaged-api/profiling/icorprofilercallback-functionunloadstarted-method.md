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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1c1c9a15e9f56765710ffb2015a29b4206b3bd4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59152604"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="0e79a-102">ICorProfilerCallback::FunctionUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="0e79a-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="0e79a-103">Oznámí profileru, modul runtime byla spuštěna uvolnit funkci.</span><span class="sxs-lookup"><span data-stu-id="0e79a-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e79a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e79a-104">Syntax</span></span>  
  
```  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="0e79a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0e79a-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="0e79a-106">[in] ID funkce, která uvolňován.</span><span class="sxs-lookup"><span data-stu-id="0e79a-106">[in] The ID of the function that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e79a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0e79a-107">Remarks</span></span>  
 <span data-ttu-id="0e79a-108">Hodnota `functionId` parametr již není platný po návratu tato metoda volajícímu.</span><span class="sxs-lookup"><span data-stu-id="0e79a-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e79a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0e79a-109">Requirements</span></span>  
 <span data-ttu-id="0e79a-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e79a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e79a-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0e79a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0e79a-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e79a-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0e79a-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0e79a-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0e79a-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e79a-114">See also</span></span>

- [<span data-ttu-id="0e79a-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e79a-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
