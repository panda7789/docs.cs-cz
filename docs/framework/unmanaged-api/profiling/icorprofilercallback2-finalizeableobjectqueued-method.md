---
title: ICorProfilerCallback2::FinalizeableObjectQueued – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.FinalizeableObjectQueued
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::FinalizeableObjectQueued
helpviewer_keywords:
- FinalizeableObjectQueued method [.NET Framework profiling]
- ICorProfilerCallback2::FinalizeableObjectQueued method [.NET Framework profiling]
ms.assetid: 92d76893-683c-475d-9996-5bff03cdb10f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e4d10b313adc60e2b851d32aeea70e2993480b0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451805"
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a><span data-ttu-id="5a4d8-102">ICorProfilerCallback2::FinalizeableObjectQueued – metoda</span><span class="sxs-lookup"><span data-stu-id="5a4d8-102">ICorProfilerCallback2::FinalizeableObjectQueued Method</span></span>
<span data-ttu-id="5a4d8-103">Kód profileru upozorní, že objekt s finalizační metody má finalizační metodu vlákno pro spuštění ve frontě jeho `Finalize` metoda.</span><span class="sxs-lookup"><span data-stu-id="5a4d8-103">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a4d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a4d8-104">Syntax</span></span>  
  
```  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a4d8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a4d8-105">Parameters</span></span>  
 `finalizerFlags`  
 <span data-ttu-id="5a4d8-106">[v] Hodnota [COR_PRF_FINALIZER_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md) výčet, který popisuje aspekty finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="5a4d8-106">[in] A value of the [COR_PRF_FINALIZER_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md) enumeration that describes aspects of the finalizer.</span></span>  
  
 `objectID`  
 <span data-ttu-id="5a4d8-107">[v] ID objektu, která byla zařazena do fronty.</span><span class="sxs-lookup"><span data-stu-id="5a4d8-107">[in] The ID of the object that has been queued.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a4d8-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5a4d8-108">Requirements</span></span>  
 <span data-ttu-id="5a4d8-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a4d8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a4d8-110">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5a4d8-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5a4d8-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a4d8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a4d8-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a4d8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a4d8-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a4d8-113">See Also</span></span>  
 [<span data-ttu-id="5a4d8-114">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a4d8-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="5a4d8-115">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a4d8-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
