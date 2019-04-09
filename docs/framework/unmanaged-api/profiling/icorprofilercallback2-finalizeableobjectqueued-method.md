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
ms.openlocfilehash: b99a942d5c5fb205a84dd3766c99cc1126998de8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190392"
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a><span data-ttu-id="f59c7-102">ICorProfilerCallback2::FinalizeableObjectQueued – metoda</span><span class="sxs-lookup"><span data-stu-id="f59c7-102">ICorProfilerCallback2::FinalizeableObjectQueued Method</span></span>
<span data-ttu-id="f59c7-103">Upozornění profileru kódu, že objekt s finalizační metody se zařadila do vlákna finalizační metody pro provádění jeho `Finalize` metoda.</span><span class="sxs-lookup"><span data-stu-id="f59c7-103">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f59c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f59c7-104">Syntax</span></span>  
  
```  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f59c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f59c7-105">Parameters</span></span>  
 `finalizerFlags`  
 <span data-ttu-id="f59c7-106">[in] Hodnota [cor_prf_finalizer_flags –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md) výčet, který popisuje aspekty finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="f59c7-106">[in] A value of the [COR_PRF_FINALIZER_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md) enumeration that describes aspects of the finalizer.</span></span>  
  
 `objectID`  
 <span data-ttu-id="f59c7-107">[in] ID objektu, která byla zařazena do fronty.</span><span class="sxs-lookup"><span data-stu-id="f59c7-107">[in] The ID of the object that has been queued.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f59c7-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f59c7-108">Requirements</span></span>  
 <span data-ttu-id="f59c7-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f59c7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f59c7-110">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f59c7-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f59c7-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f59c7-111">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f59c7-112">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f59c7-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f59c7-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f59c7-113">See also</span></span>

- [<span data-ttu-id="f59c7-114">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f59c7-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="f59c7-115">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f59c7-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
