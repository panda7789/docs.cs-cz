---
title: "ICorProfilerCallback2::FinalizeableObjectQueued – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.FinalizeableObjectQueued
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::FinalizeableObjectQueued
helpviewer_keywords:
- FinalizeableObjectQueued method [.NET Framework profiling]
- ICorProfilerCallback2::FinalizeableObjectQueued method [.NET Framework profiling]
ms.assetid: 92d76893-683c-475d-9996-5bff03cdb10f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7ff90fd6df337f7b92a73b43b6abc488da7ed6b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a><span data-ttu-id="57ad6-102">ICorProfilerCallback2::FinalizeableObjectQueued – metoda</span><span class="sxs-lookup"><span data-stu-id="57ad6-102">ICorProfilerCallback2::FinalizeableObjectQueued Method</span></span>
<span data-ttu-id="57ad6-103">Kód profileru upozorní, že objekt s finalizační metody má finalizační metodu vlákno pro spuštění ve frontě jeho `Finalize` metoda.</span><span class="sxs-lookup"><span data-stu-id="57ad6-103">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57ad6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57ad6-104">Syntax</span></span>  
  
```  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57ad6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57ad6-105">Parameters</span></span>  
 `finalizerFlags`  
 <span data-ttu-id="57ad6-106">[v] Hodnota [COR_PRF_FINALIZER_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md) výčet, který popisuje aspekty finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="57ad6-106">[in] A value of the [COR_PRF_FINALIZER_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md) enumeration that describes aspects of the finalizer.</span></span>  
  
 `objectID`  
 <span data-ttu-id="57ad6-107">[v] ID objektu, která byla zařazena do fronty.</span><span class="sxs-lookup"><span data-stu-id="57ad6-107">[in] The ID of the object that has been queued.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57ad6-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57ad6-108">Requirements</span></span>  
 <span data-ttu-id="57ad6-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57ad6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57ad6-110">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="57ad6-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="57ad6-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57ad6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57ad6-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57ad6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57ad6-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="57ad6-113">See Also</span></span>  
 [<span data-ttu-id="57ad6-114">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57ad6-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="57ad6-115">Icorprofilercallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57ad6-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
