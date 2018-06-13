---
title: ICorProfilerCallback::Initialize – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Initialize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cd53d74dfe8199617df47e46641b71203abf6e5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452345"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="11fb9-102">ICorProfilerCallback::Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="11fb9-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="11fb9-103">Volat za účelem inicializace profileru kód při každém spuštění nové aplikace běžné runtime (CLR) jazyk.</span><span class="sxs-lookup"><span data-stu-id="11fb9-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11fb9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11fb9-104">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="11fb9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="11fb9-105">Parameters</span></span>  
 `pICorProfilerInfoUnk`  
 <span data-ttu-id="11fb9-106">[v](/cpp/atl/iunknown) rozhraní, které musí vyhledat profileru [icorprofilerinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) ukazatel rozhraní.</span><span class="sxs-lookup"><span data-stu-id="11fb9-106">[in](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11fb9-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11fb9-107">Remarks</span></span>  
 <span data-ttu-id="11fb9-108">`Initialize` Volání je pouze možnost povolit (nebo zakázat) zpětná volání, které jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="11fb9-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="11fb9-109">Jakmile povolíte zpětné volání pomocí `Initialize` volat, nelze zakázat, později pomocí [icorprofilerinfo::seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span><span class="sxs-lookup"><span data-stu-id="11fb9-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="11fb9-110">Hodnota COR_PRF_MONITOR_IMMUTABLE [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčet Určuje události, které jsou neměnné.</span><span class="sxs-lookup"><span data-stu-id="11fb9-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11fb9-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="11fb9-111">Requirements</span></span>  
 <span data-ttu-id="11fb9-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11fb9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11fb9-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="11fb9-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="11fb9-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11fb9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11fb9-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11fb9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11fb9-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="11fb9-116">See Also</span></span>  
 [<span data-ttu-id="11fb9-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11fb9-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="11fb9-118">Shutdown – metoda</span><span class="sxs-lookup"><span data-stu-id="11fb9-118">Shutdown Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)
