---
title: ICorProfilerCallback2::GarbageCollectionFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished
helpviewer_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished method [.NET Framework profiling]
- GarbageCollectionFinished method [.NET Framework profiling]
ms.assetid: 1a5758ea-2354-43c0-92a3-32c9909d64e1
topic_type:
- apiref
ms.openlocfilehash: 47f25dbb1f88dbf580b096246016cd46f2d0d89c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499820"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="f1677-102">ICorProfilerCallback2::GarbageCollectionFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="f1677-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="f1677-103">Upozorní profileru, že uvolňování paměti bylo dokončeno a že pro něj byly vydány všechna zpětná volání uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f1677-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1677-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1677-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f1677-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f1677-105">Remarks</span></span>  
 <span data-ttu-id="f1677-106">Je bezpečné, aby Profiler zkontroloval objekty v jejich finálních umístěních při `GarbageCollectionFinished` volání metody.</span><span class="sxs-lookup"><span data-stu-id="f1677-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1677-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f1677-107">Requirements</span></span>  
 <span data-ttu-id="f1677-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1677-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1677-109">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f1677-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f1677-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f1677-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1677-111">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1677-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1677-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1677-112">See also</span></span>

- [<span data-ttu-id="f1677-113">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1677-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="f1677-114">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1677-114">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
