---
title: ICorProfilerCallback::ModuleUnloadFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f7759b0815946301932ca60edaf731313d04a245
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743462"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="912c7-102">ICorProfilerCallback::ModuleUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="912c7-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>
<span data-ttu-id="912c7-103">Upozorní profiler modulu dokončení uvolnění.</span><span class="sxs-lookup"><span data-stu-id="912c7-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="912c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="912c7-104">Syntax</span></span>  
  
```  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="912c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="912c7-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="912c7-106">[in] ID modulu, který byl odpojen.</span><span class="sxs-lookup"><span data-stu-id="912c7-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="912c7-107">[in] HRESULT, která určuje, zda modul byl uvolněn úspěšně.</span><span class="sxs-lookup"><span data-stu-id="912c7-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="912c7-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="912c7-108">Remarks</span></span>  
 <span data-ttu-id="912c7-109">Hodnota `moduleId` není platná pro požadavek informace po [icorprofilercallback::moduleunloadstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) metoda vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="912c7-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="912c7-110">Některé části uvolnění třídy může pokračovat po `ModuleUnloadFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="912c7-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="912c7-111">Selhání hodnoty HRESULT v `hrStatus` naznačuje chybu.</span><span class="sxs-lookup"><span data-stu-id="912c7-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="912c7-112">Ale úspěch HRESULT v `hrStatus` značí pouze, že první část uvolnění modulu proběhla úspěšně.</span><span class="sxs-lookup"><span data-stu-id="912c7-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="912c7-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="912c7-113">Requirements</span></span>  
 <span data-ttu-id="912c7-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="912c7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="912c7-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="912c7-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="912c7-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="912c7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="912c7-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="912c7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="912c7-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="912c7-118">See also</span></span>
- [<span data-ttu-id="912c7-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="912c7-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
