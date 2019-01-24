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
ms.openlocfilehash: deb8475ab338c6ce733f1700e509dff982bd697f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611173"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="66529-102">ICorProfilerCallback::AssemblyLoadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="66529-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="66529-103">Načtení sestavení oznámí profileru.</span><span class="sxs-lookup"><span data-stu-id="66529-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66529-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66529-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66529-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66529-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="66529-106">[in] Určuje sestavení, který se načítá.</span><span class="sxs-lookup"><span data-stu-id="66529-106">[in] Identifies the assembly that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66529-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66529-107">Remarks</span></span>  
 <span data-ttu-id="66529-108">Hodnota `assemblyId` není platná pro požadavek informace do [icorprofilercallback::assemblyloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="66529-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66529-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66529-109">Requirements</span></span>  
 <span data-ttu-id="66529-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66529-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66529-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="66529-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="66529-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66529-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66529-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66529-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66529-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66529-114">See also</span></span>
- [<span data-ttu-id="66529-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66529-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
