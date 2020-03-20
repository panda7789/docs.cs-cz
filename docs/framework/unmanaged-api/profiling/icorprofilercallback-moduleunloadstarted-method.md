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
ms.openlocfilehash: fcfdddbd5316c098754ea7b0d4714b050c64fe55
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175145"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="9fa74-102">ICorProfilerCallback::ModuleUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="9fa74-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="9fa74-103">Upozorní profiler, že modul je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="9fa74-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fa74-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fa74-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);
```  
  
## <a name="parameters"></a><span data-ttu-id="9fa74-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9fa74-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="9fa74-106">[v] ID modulu, který je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="9fa74-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9fa74-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9fa74-107">Remarks</span></span>  
 <span data-ttu-id="9fa74-108">Hodnota `moduleId` není platná pro požadavek na `ModuleUnloadStarted` informace po vrátí metoda – toto je profiler poslední šanci získat informace o tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="9fa74-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fa74-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9fa74-109">Requirements</span></span>  
 <span data-ttu-id="9fa74-110">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fa74-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fa74-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9fa74-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9fa74-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9fa74-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9fa74-113">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fa74-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fa74-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="9fa74-114">See also</span></span>

- [<span data-ttu-id="9fa74-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9fa74-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="9fa74-116">ModuleUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="9fa74-116">ModuleUnloadFinished Method</span></span>](icorprofilercallback-moduleunloadfinished-method.md)
