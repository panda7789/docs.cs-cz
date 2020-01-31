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
ms.openlocfilehash: 7e43f58f619aaa63fa2294dd3e989026dcdfc604
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866127"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="c9214-102">ICorProfilerCallback::ModuleUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="c9214-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="c9214-103">Upozorní profileru, že je modul uvolňován.</span><span class="sxs-lookup"><span data-stu-id="c9214-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9214-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9214-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="c9214-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9214-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="c9214-106">pro ID modulu, který se má uvolnit</span><span class="sxs-lookup"><span data-stu-id="c9214-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9214-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c9214-107">Remarks</span></span>  
 <span data-ttu-id="c9214-108">Hodnota `moduleId` není platná pro požadavek na informace po návratu metody `ModuleUnloadStarted` – jedná se o poslední možnost profileru získat informace o tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="c9214-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9214-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9214-109">Requirements</span></span>  
 <span data-ttu-id="c9214-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9214-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9214-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c9214-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c9214-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c9214-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9214-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9214-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9214-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9214-114">See also</span></span>

- [<span data-ttu-id="c9214-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9214-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c9214-116">ModuleUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="c9214-116">ModuleUnloadFinished Method</span></span>](icorprofilercallback-moduleunloadfinished-method.md)
