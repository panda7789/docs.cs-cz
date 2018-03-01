---
title: "ICorProfilerCallback::JITFunctionPitched – metoda"
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
- ICorProfilerCallback.JITFunctionPitched
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 48432911d7844e6519689961c985da37219179a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="90ab1-102">ICorProfilerCallback::JITFunctionPitched – metoda</span><span class="sxs-lookup"><span data-stu-id="90ab1-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>
<span data-ttu-id="90ab1-103">Upozorní profileru, funkci, která byla v běhu (JIT)-zkompilovat byl odebrán z paměti.</span><span class="sxs-lookup"><span data-stu-id="90ab1-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90ab1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90ab1-104">Syntax</span></span>  
  
```  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90ab1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="90ab1-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="90ab1-106">[v] ID funkce, která byla odebrána.</span><span class="sxs-lookup"><span data-stu-id="90ab1-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90ab1-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90ab1-107">Remarks</span></span>  
 <span data-ttu-id="90ab1-108">Pokud odebrané funkce je volána, obdrží profileru nové události JIT – kompilace při znovu zkompiluje funkce.</span><span class="sxs-lookup"><span data-stu-id="90ab1-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="90ab1-109">V současné době běžné language runtime (CLR) JIT kompilátoru neodebere funkce z paměti, tak, aby tento zpětného volání není aktuálně používá a nebude přijatých profileru.</span><span class="sxs-lookup"><span data-stu-id="90ab1-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="90ab1-110">Hodnota `functionId` není platná, dokud nebude znovu zkompiluje funkce.</span><span class="sxs-lookup"><span data-stu-id="90ab1-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="90ab1-111">Když znovu zkompiluje funkce stejné `functionId` bude použita hodnota.</span><span class="sxs-lookup"><span data-stu-id="90ab1-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90ab1-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90ab1-112">Requirements</span></span>  
 <span data-ttu-id="90ab1-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90ab1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90ab1-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="90ab1-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="90ab1-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90ab1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90ab1-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90ab1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90ab1-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="90ab1-117">See Also</span></span>  
 [<span data-ttu-id="90ab1-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90ab1-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
