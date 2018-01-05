---
title: "ICorProfilerCallback::ObjectAllocated – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ObjectAllocated
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 37f4701271f299698d7cd323b7d701f4cb7adb25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="6d33b-102">ICorProfilerCallback::ObjectAllocated – metoda</span><span class="sxs-lookup"><span data-stu-id="6d33b-102">ICorProfilerCallback::ObjectAllocated Method</span></span>
<span data-ttu-id="6d33b-103">Upozorní profileru, která se přidělí paměť v rámci haldy pro objekt.</span><span class="sxs-lookup"><span data-stu-id="6d33b-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d33b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d33b-104">Syntax</span></span>  
  
```  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d33b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d33b-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="6d33b-106">[v] ID objektu, pro kterou se přidělí paměť.</span><span class="sxs-lookup"><span data-stu-id="6d33b-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="6d33b-107">[v] ID třídy, které je objekt instance.</span><span class="sxs-lookup"><span data-stu-id="6d33b-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d33b-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d33b-108">Remarks</span></span>  
 <span data-ttu-id="6d33b-109">`ObjectedAllocated` Metoda není volána pro přidělení z zásobníku nebo nespravované paměti.</span><span class="sxs-lookup"><span data-stu-id="6d33b-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="6d33b-110">`classId` Parametr mohou odkazovat na třídu ve spravovaném kódu, která dosud nebyla načtena.</span><span class="sxs-lookup"><span data-stu-id="6d33b-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="6d33b-111">Profileru obdrží zpětné volání – třída zatížení pro tuto třídu ihned po `ObjectAllocated` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="6d33b-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d33b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6d33b-112">Requirements</span></span>  
 <span data-ttu-id="6d33b-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d33b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d33b-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6d33b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6d33b-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d33b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d33b-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d33b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d33b-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d33b-117">See Also</span></span>  
 [<span data-ttu-id="6d33b-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6d33b-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="6d33b-119">ClassLoadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="6d33b-119">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)  
 [<span data-ttu-id="6d33b-120">ClassLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="6d33b-120">ClassLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)
