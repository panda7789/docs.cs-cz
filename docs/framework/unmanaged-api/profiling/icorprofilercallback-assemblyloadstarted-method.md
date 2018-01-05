---
title: "ICorProfilerCallback::AssemblyLoadStarted – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AssemblyLoadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AssemblyLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadStarted method [.NET Framework profiling]
- AssemblyLoadStarted method [.NET Framework profiling]
ms.assetid: 67e8209d-a0ca-4118-a6e6-c1ee0abc2221
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 48453532177b1e619f4f863e7297345566637d4f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="46c3a-102">ICorProfilerCallback::AssemblyLoadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="46c3a-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="46c3a-103">Upozorní profileru se načítá sestavení.</span><span class="sxs-lookup"><span data-stu-id="46c3a-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46c3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46c3a-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="46c3a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="46c3a-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="46c3a-106">[v] Identifikuje sestavení, které je právě načítán.</span><span class="sxs-lookup"><span data-stu-id="46c3a-106">[in] Identifies the assembly that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46c3a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="46c3a-107">Remarks</span></span>  
 <span data-ttu-id="46c3a-108">Hodnota `assemblyId` není platná pro požadavek informace, dokud [icorprofilercallback::assemblyloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="46c3a-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46c3a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="46c3a-109">Requirements</span></span>  
 <span data-ttu-id="46c3a-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46c3a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46c3a-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="46c3a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="46c3a-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46c3a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46c3a-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46c3a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46c3a-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="46c3a-114">See Also</span></span>  
 [<span data-ttu-id="46c3a-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46c3a-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
