---
title: ICorProfilerCallback::ClassUnloadStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type:
- apiref
ms.openlocfilehash: 3b729d3be84571a48cc9a770d7f06b99723c0d1f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445063"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="6eeff-102">ICorProfilerCallback::ClassUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="6eeff-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="6eeff-103">Notifies the profiler that a class is being unloaded.</span><span class="sxs-lookup"><span data-stu-id="6eeff-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eeff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6eeff-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6eeff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6eeff-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="6eeff-106">[in] Identifies the class that is being unloaded.</span><span class="sxs-lookup"><span data-stu-id="6eeff-106">[in] Identifies the class that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6eeff-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6eeff-107">Remarks</span></span>  
 <span data-ttu-id="6eeff-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span><span class="sxs-lookup"><span data-stu-id="6eeff-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6eeff-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6eeff-109">Requirements</span></span>  
 <span data-ttu-id="6eeff-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6eeff-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6eeff-111">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6eeff-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6eeff-112">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6eeff-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6eeff-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6eeff-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eeff-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6eeff-114">See also</span></span>

- [<span data-ttu-id="6eeff-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6eeff-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="6eeff-116">ClassUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="6eeff-116">ClassUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)
