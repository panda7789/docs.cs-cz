---
title: ICorProfilerCallback::ModuleUnloadStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadStarted
helpviewer_keywords:
- ModuleUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadStarted method [.NET Framework profiling]
ms.assetid: 2debcaab-6005-4245-afdb-4268bb7e74bd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bb00a56b0d80b78867f70e64c1c9bdf0fc49e1be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041935"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="b46ef-102">ICorProfilerCallback::ModuleUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="b46ef-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="b46ef-103">Upozornění profileru uvolnění modulu.</span><span class="sxs-lookup"><span data-stu-id="b46ef-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b46ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b46ef-104">Syntax</span></span>  
  
```  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="b46ef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b46ef-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="b46ef-106">[in] ID modulu, který uvolňován.</span><span class="sxs-lookup"><span data-stu-id="b46ef-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b46ef-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b46ef-107">Remarks</span></span>  
 <span data-ttu-id="b46ef-108">Hodnota `moduleId` není platná pro požadavek informace po `ModuleUnloadStarted` metoda vrátí hodnotu – Toto je poslední možnost profileru a získat informace o tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="b46ef-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b46ef-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b46ef-109">Requirements</span></span>  
 <span data-ttu-id="b46ef-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b46ef-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b46ef-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b46ef-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b46ef-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b46ef-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b46ef-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b46ef-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b46ef-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b46ef-114">See also</span></span>

- [<span data-ttu-id="b46ef-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b46ef-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="b46ef-116">ModuleUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="b46ef-116">ModuleUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)
