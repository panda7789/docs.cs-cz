---
title: "ICorProfilerCallback::Initialize – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.Initialize
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2eebe596b3459d51afe66df4bb81f74e93f3526e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="8021c-102">ICorProfilerCallback::Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="8021c-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="8021c-103">Volat za účelem inicializace profileru kód při každém spuštění nové aplikace běžné runtime (CLR) jazyk.</span><span class="sxs-lookup"><span data-stu-id="8021c-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8021c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8021c-104">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8021c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8021c-105">Parameters</span></span>  
 `pICorProfilerInfoUnk`  
 <span data-ttu-id="8021c-106">[v](/cpp/atl/iunknown) rozhraní, které musí vyhledat profileru [icorprofilerinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) ukazatel rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8021c-106">[in](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8021c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8021c-107">Remarks</span></span>  
 <span data-ttu-id="8021c-108">`Initialize` Volání je pouze možnost povolit (nebo zakázat) zpětná volání, které jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="8021c-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="8021c-109">Jakmile povolíte zpětné volání pomocí `Initialize` volat, nelze zakázat, později pomocí [icorprofilerinfo::seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span><span class="sxs-lookup"><span data-stu-id="8021c-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="8021c-110">Hodnota COR_PRF_MONITOR_IMMUTABLE [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčet Určuje události, které jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="8021c-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8021c-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8021c-111">Requirements</span></span>  
 <span data-ttu-id="8021c-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8021c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8021c-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8021c-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8021c-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8021c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8021c-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8021c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8021c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="8021c-116">See Also</span></span>  
 [<span data-ttu-id="8021c-117">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8021c-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="8021c-118">Shutdown – metoda</span><span class="sxs-lookup"><span data-stu-id="8021c-118">Shutdown Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)
