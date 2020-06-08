---
title: ICorProfilerCallback2::HandleDestroyed – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.HandleDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::HandleDestroyed
helpviewer_keywords:
- ICorProfilerCallback2::HandleDestroyed method [.NET Framework profiling]
- HandleDestroyed method [.NET Framework profiling]
ms.assetid: ab4f4bbd-40c7-4667-bfde-60cd73803110
topic_type:
- apiref
ms.openlocfilehash: d7a4f7d08e6d8698dbb58c4c2d111a47d0ccc8db
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499776"
---
# <a name="icorprofilercallback2handledestroyed-method"></a><span data-ttu-id="361cb-102">ICorProfilerCallback2::HandleDestroyed – metoda</span><span class="sxs-lookup"><span data-stu-id="361cb-102">ICorProfilerCallback2::HandleDestroyed Method</span></span>
<span data-ttu-id="361cb-103">Upozorní profiler kódu, že byl zničen popisovač uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="361cb-103">Notifies the code profiler that a garbage collection handle has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="361cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="361cb-104">Syntax</span></span>  
  
```cpp  
HRESULT HandleDestroyed(  
    [in] GCHandleID handleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="361cb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="361cb-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="361cb-106">pro ID popisovače pro uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="361cb-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="361cb-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="361cb-107">Requirements</span></span>  
 <span data-ttu-id="361cb-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="361cb-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="361cb-109">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="361cb-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="361cb-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="361cb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="361cb-111">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="361cb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="361cb-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="361cb-112">See also</span></span>

- [<span data-ttu-id="361cb-113">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="361cb-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="361cb-114">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="361cb-114">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
