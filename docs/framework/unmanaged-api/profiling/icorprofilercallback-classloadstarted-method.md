---
title: ICorProfilerCallback::ClassLoadStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::ClassLoadStarted method [.NET Framework profiling]
- ClassLoadStarted method [.NET Framework profiling]
ms.assetid: 9f728de8-45c2-45a5-ac4a-45660bd36ecf
topic_type:
- apiref
ms.openlocfilehash: 9a9fdc80c8f63dd5b004953266a5d7399655bc71
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500361"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="6c28e-102">ICorProfilerCallback::ClassLoadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="6c28e-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="6c28e-103">Upozorní profileru, že je načtena třída.</span><span class="sxs-lookup"><span data-stu-id="6c28e-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c28e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c28e-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c28e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c28e-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="6c28e-106">\[v] identifikuje třídu, která je načítána.</span><span class="sxs-lookup"><span data-stu-id="6c28e-106">\[in] Identifies the class that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="6c28e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c28e-107">Remarks</span></span>  
 <span data-ttu-id="6c28e-108">Hodnota `classId` není platná pro požadavek na informace, dokud není volána metoda [ICorProfilerCallback:: ClassLoadFinished –](icorprofilercallback-classloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6c28e-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c28e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6c28e-109">Requirements</span></span>  
 <span data-ttu-id="6c28e-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c28e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c28e-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6c28e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6c28e-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6c28e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c28e-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c28e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c28e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c28e-114">See also</span></span>

- [<span data-ttu-id="6c28e-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c28e-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
