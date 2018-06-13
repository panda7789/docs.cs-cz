---
title: ICorProfilerCallback::AssemblyLoadStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadStarted method [.NET Framework profiling]
- AssemblyLoadStarted method [.NET Framework profiling]
ms.assetid: 67e8209d-a0ca-4118-a6e6-c1ee0abc2221
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af40d8b603d3bd13abbc5a1c06464583bfa7842d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450216"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="9c09c-102">ICorProfilerCallback::AssemblyLoadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="9c09c-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="9c09c-103">Upozorní profileru se načítá sestavení.</span><span class="sxs-lookup"><span data-stu-id="9c09c-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c09c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c09c-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c09c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c09c-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="9c09c-106">[v] Identifikuje sestavení, které je právě načítán.</span><span class="sxs-lookup"><span data-stu-id="9c09c-106">[in] Identifies the assembly that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c09c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9c09c-107">Remarks</span></span>  
 <span data-ttu-id="9c09c-108">Hodnota `assemblyId` není platná pro požadavek informace, dokud [icorprofilercallback::assemblyloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="9c09c-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c09c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9c09c-109">Requirements</span></span>  
 <span data-ttu-id="9c09c-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c09c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c09c-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9c09c-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9c09c-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c09c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c09c-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c09c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c09c-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c09c-114">See Also</span></span>  
 [<span data-ttu-id="9c09c-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c09c-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
