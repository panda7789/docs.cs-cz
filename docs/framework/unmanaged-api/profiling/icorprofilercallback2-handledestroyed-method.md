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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57b814f01d7da8d5b3f9e5bda7d0cf517bb870ed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592312"
---
# <a name="icorprofilercallback2handledestroyed-method"></a><span data-ttu-id="9fc7b-102">ICorProfilerCallback2::HandleDestroyed – metoda</span><span class="sxs-lookup"><span data-stu-id="9fc7b-102">ICorProfilerCallback2::HandleDestroyed Method</span></span>
<span data-ttu-id="9fc7b-103">Upozornění profileru kód zlikvidování popisovač kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="9fc7b-103">Notifies the code profiler that a garbage collection handle has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fc7b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fc7b-104">Syntax</span></span>  
  
```  
HRESULT HandleDestroyed(  
    [in] GCHandleID handleId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9fc7b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9fc7b-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="9fc7b-106">[in] ID popisovač pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="9fc7b-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fc7b-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9fc7b-107">Requirements</span></span>  
 <span data-ttu-id="9fc7b-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fc7b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fc7b-109">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9fc7b-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9fc7b-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9fc7b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9fc7b-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fc7b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fc7b-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9fc7b-112">See also</span></span>
- [<span data-ttu-id="9fc7b-113">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9fc7b-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="9fc7b-114">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9fc7b-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
