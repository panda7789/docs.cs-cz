---
title: ICorProfilerCallback::ObjectAllocated – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectAllocated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c7d62b1b6031f6ebdd5327626f42de38b18b3fa7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452046"
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="78876-102">ICorProfilerCallback::ObjectAllocated – metoda</span><span class="sxs-lookup"><span data-stu-id="78876-102">ICorProfilerCallback::ObjectAllocated Method</span></span>
<span data-ttu-id="78876-103">Upozorní profileru, která se přidělí paměť v rámci haldy pro objekt.</span><span class="sxs-lookup"><span data-stu-id="78876-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78876-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78876-104">Syntax</span></span>  
  
```  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78876-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78876-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="78876-106">[v] ID objektu, pro kterou se přidělí paměť.</span><span class="sxs-lookup"><span data-stu-id="78876-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="78876-107">[v] ID třídy, které je objekt instance.</span><span class="sxs-lookup"><span data-stu-id="78876-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78876-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="78876-108">Remarks</span></span>  
 <span data-ttu-id="78876-109">`ObjectedAllocated` Metoda není volána pro přidělení z zásobníku nebo nespravované paměti.</span><span class="sxs-lookup"><span data-stu-id="78876-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="78876-110">`classId` Parametr mohou odkazovat na třídu ve spravovaném kódu, která dosud nebyla načtena.</span><span class="sxs-lookup"><span data-stu-id="78876-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="78876-111">Profileru obdrží zpětné volání – třída zatížení pro tuto třídu ihned po `ObjectAllocated` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="78876-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78876-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78876-112">Requirements</span></span>  
 <span data-ttu-id="78876-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78876-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78876-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="78876-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="78876-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78876-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78876-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78876-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78876-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="78876-117">See Also</span></span>  
 [<span data-ttu-id="78876-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78876-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="78876-119">ClassLoadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="78876-119">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)  
 [<span data-ttu-id="78876-120">ClassLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="78876-120">ClassLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)
