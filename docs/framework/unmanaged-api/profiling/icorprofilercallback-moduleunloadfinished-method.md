---
title: "ICorProfilerCallback::ModuleUnloadFinished – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleUnloadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: dc97a4173e384622fefa7de528a9725b68923ff2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="c99ac-102">ICorProfilerCallback::ModuleUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="c99ac-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>
<span data-ttu-id="c99ac-103">Aby modul dokončil uvolnění upozorní profileru.</span><span class="sxs-lookup"><span data-stu-id="c99ac-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c99ac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c99ac-104">Syntax</span></span>  
  
```  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c99ac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c99ac-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="c99ac-106">[v] ID modul, který byl odpojen.</span><span class="sxs-lookup"><span data-stu-id="c99ac-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="c99ac-107">[v] HRESULT, která určuje, zda byl modul úspěšně odpojen.</span><span class="sxs-lookup"><span data-stu-id="c99ac-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c99ac-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c99ac-108">Remarks</span></span>  
 <span data-ttu-id="c99ac-109">Hodnota `moduleId` není platná pro požadavek informace po [icorprofilercallback::moduleunloadstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="c99ac-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="c99ac-110">Některé části uvolnění třídy, může pokračovat i po `ModuleUnloadFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="c99ac-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="c99ac-111">Selhání HRESULT v `hrStatus` znamená chybu.</span><span class="sxs-lookup"><span data-stu-id="c99ac-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="c99ac-112">Ale úspěšné HRESULT v `hrStatus` pouze označuje, že první část uvolnění modulu proběhl úspěšně.</span><span class="sxs-lookup"><span data-stu-id="c99ac-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c99ac-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c99ac-113">Requirements</span></span>  
 <span data-ttu-id="c99ac-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c99ac-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c99ac-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c99ac-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c99ac-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c99ac-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c99ac-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c99ac-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c99ac-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="c99ac-118">See Also</span></span>  
 [<span data-ttu-id="c99ac-119">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c99ac-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
