---
title: "ICorProfilerCallback::ModuleLoadStarted – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 09f88b2a287eef0bf3fe8edeba4b76a3b3a1ce4a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="a292e-102">ICorProfilerCallback::ModuleLoadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="a292e-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>
<span data-ttu-id="a292e-103">Aby modul načítá upozorní profileru.</span><span class="sxs-lookup"><span data-stu-id="a292e-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a292e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a292e-104">Syntax</span></span>  
  
```  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a292e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a292e-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="a292e-106">[v] ID modul, který je právě načítán.</span><span class="sxs-lookup"><span data-stu-id="a292e-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a292e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a292e-107">Remarks</span></span>  
 <span data-ttu-id="a292e-108">Hodnota `moduleId` není platná pro požadavek informace, dokud [icorprofilercallback::moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="a292e-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a292e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a292e-109">Requirements</span></span>  
 <span data-ttu-id="a292e-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a292e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a292e-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a292e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a292e-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a292e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a292e-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a292e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a292e-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="a292e-114">See Also</span></span>  
 [<span data-ttu-id="a292e-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a292e-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
