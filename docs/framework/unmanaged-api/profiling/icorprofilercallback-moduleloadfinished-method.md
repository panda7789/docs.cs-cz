---
title: "ICorProfilerCallback::ModuleLoadFinished – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleLoadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 360c14ccdd67cb7609ffe2f9c49914fdda163389
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="f3285-102">ICorProfilerCallback::ModuleLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="f3285-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="f3285-103">Aby modul dokončil načítání upozorní profileru.</span><span class="sxs-lookup"><span data-stu-id="f3285-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3285-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3285-104">Syntax</span></span>  
  
```  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3285-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3285-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="f3285-106">[v] ID modul, který dokončil načítání.</span><span class="sxs-lookup"><span data-stu-id="f3285-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="f3285-107">[v] HRESULT, která určuje, zda modul byl úspěšně načten.</span><span class="sxs-lookup"><span data-stu-id="f3285-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3285-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3285-108">Remarks</span></span>  
 <span data-ttu-id="f3285-109">Hodnota `moduleId` není platná pro požadavek informace, dokud `ModuleLoadFinished` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="f3285-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="f3285-110">Některé části načítání modulu může pokračovat po `ModuleLoadFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="f3285-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="f3285-111">Selhání HRESULT v `hrStatus` znamená chybu.</span><span class="sxs-lookup"><span data-stu-id="f3285-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="f3285-112">Ale úspěšné HRESULT v `hrStatus` pouze označuje, že první část načítání modulu proběhl úspěšně.</span><span class="sxs-lookup"><span data-stu-id="f3285-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3285-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f3285-113">Requirements</span></span>  
 <span data-ttu-id="f3285-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3285-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3285-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f3285-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f3285-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3285-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3285-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3285-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3285-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3285-118">See Also</span></span>  
 [<span data-ttu-id="f3285-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3285-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="f3285-120">ModuleLoadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="f3285-120">ModuleLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
