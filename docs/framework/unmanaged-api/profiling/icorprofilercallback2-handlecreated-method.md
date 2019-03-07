---
title: ICorProfilerCallback2::HandleCreated – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.HandleCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::HandleCreated
helpviewer_keywords:
- HandleCreated method [.NET Framework profiling]
- ICorProfilerCallback2::HandleCreated method [.NET Framework profiling]
ms.assetid: 6bbb7786-7c38-490f-9834-91aa2795c355
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e598c4f3a4f777cdb8a871cdc6ea56a080e3c9bc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496908"
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="638d7-102">ICorProfilerCallback2::HandleCreated – metoda</span><span class="sxs-lookup"><span data-stu-id="638d7-102">ICorProfilerCallback2::HandleCreated Method</span></span>
<span data-ttu-id="638d7-103">Upozornění profileru kódu, není vytvořen popisovač kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="638d7-103">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="638d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="638d7-104">Syntax</span></span>  
  
```  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="638d7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="638d7-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="638d7-106">[in] ID popisovač pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="638d7-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="638d7-107">[in] ID objektu, pro který byl vytvořen popisovač kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="638d7-107">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="638d7-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="638d7-108">Requirements</span></span>  
 <span data-ttu-id="638d7-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="638d7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="638d7-110">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="638d7-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="638d7-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="638d7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="638d7-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="638d7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="638d7-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="638d7-113">See also</span></span>
- [<span data-ttu-id="638d7-114">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="638d7-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="638d7-115">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="638d7-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
