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
ms.openlocfilehash: 38d9e83e9fa0e9cd0586fb10a6fd79c29bead4a6
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866101"
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="06d4e-102">ICorProfilerCallback::ObjectAllocated – metoda</span><span class="sxs-lookup"><span data-stu-id="06d4e-102">ICorProfilerCallback::ObjectAllocated Method</span></span>
<span data-ttu-id="06d4e-103">Upozorní profileru, že paměť v haldě byla přidělena pro objekt.</span><span class="sxs-lookup"><span data-stu-id="06d4e-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06d4e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06d4e-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06d4e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06d4e-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="06d4e-106">pro ID objektu, pro který byla přidělena paměť</span><span class="sxs-lookup"><span data-stu-id="06d4e-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="06d4e-107">pro ID třídy, jejíž objekt je instancí.</span><span class="sxs-lookup"><span data-stu-id="06d4e-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06d4e-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="06d4e-108">Remarks</span></span>  
 <span data-ttu-id="06d4e-109">Metoda `ObjectedAllocated` není volána pro přidělení z zásobníku nebo nespravované paměti.</span><span class="sxs-lookup"><span data-stu-id="06d4e-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="06d4e-110">Parametr `classId` může odkazovat na třídu ve spravovaném kódu, která ještě nebyla načtena.</span><span class="sxs-lookup"><span data-stu-id="06d4e-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="06d4e-111">Profiler obdrží zpětné volání třídy pro tuto třídu hned po zpětném volání `ObjectAllocated`.</span><span class="sxs-lookup"><span data-stu-id="06d4e-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06d4e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="06d4e-112">Requirements</span></span>  
 <span data-ttu-id="06d4e-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06d4e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06d4e-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="06d4e-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="06d4e-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="06d4e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06d4e-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06d4e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06d4e-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06d4e-117">See also</span></span>

- [<span data-ttu-id="06d4e-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="06d4e-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="06d4e-119">ClassLoadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="06d4e-119">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
- [<span data-ttu-id="06d4e-120">ClassLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="06d4e-120">ClassLoadFinished Method</span></span>](icorprofilercallback-classloadfinished-method.md)
