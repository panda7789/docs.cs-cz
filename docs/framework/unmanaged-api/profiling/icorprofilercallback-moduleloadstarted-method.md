---
title: ICorProfilerCallback::ModuleLoadStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadStarted
helpviewer_keywords:
- ModuleLoadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadStarted method [.NET Framework profiling]
ms.assetid: 9cd2fe75-408a-400f-a6b1-9979624a2fe2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3503aa1eb86246365e31f52313893ad8713f5748
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153683"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="87ea7-102">ICorProfilerCallback::ModuleLoadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="87ea7-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>
<span data-ttu-id="87ea7-103">Oznámí profileru, načtení modulu.</span><span class="sxs-lookup"><span data-stu-id="87ea7-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87ea7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87ea7-104">Syntax</span></span>  
  
```  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87ea7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="87ea7-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="87ea7-106">[in] ID modulu, který se načítá.</span><span class="sxs-lookup"><span data-stu-id="87ea7-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87ea7-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="87ea7-107">Remarks</span></span>  
 <span data-ttu-id="87ea7-108">Hodnota `moduleId` není platná pro požadavek informace do [icorprofilercallback::moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="87ea7-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87ea7-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="87ea7-109">Requirements</span></span>  
 <span data-ttu-id="87ea7-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87ea7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87ea7-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="87ea7-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="87ea7-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87ea7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87ea7-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87ea7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87ea7-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87ea7-114">See also</span></span>

- [<span data-ttu-id="87ea7-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87ea7-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
