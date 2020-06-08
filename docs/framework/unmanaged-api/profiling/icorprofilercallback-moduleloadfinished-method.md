---
title: ICorProfilerCallback::ModuleLoadFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type:
- apiref
ms.openlocfilehash: 481fc2c40331e31f6a018d012fb2b2543d4fd9b5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503364"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="938a1-102">ICorProfilerCallback::ModuleLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="938a1-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="938a1-103">Upozorní profileru, že se dokončilo načítání modulu.</span><span class="sxs-lookup"><span data-stu-id="938a1-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="938a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="938a1-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="938a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="938a1-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="938a1-106">pro ID modulu, který dokončil načítání.</span><span class="sxs-lookup"><span data-stu-id="938a1-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="938a1-107">pro Hodnota HRESULT, která označuje, zda byl modul úspěšně načten.</span><span class="sxs-lookup"><span data-stu-id="938a1-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="938a1-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="938a1-108">Remarks</span></span>  
 <span data-ttu-id="938a1-109">Hodnota `moduleId` není platná pro požadavek na informace, dokud `ModuleLoadFinished` není volána metoda.</span><span class="sxs-lookup"><span data-stu-id="938a1-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="938a1-110">Některé části načtení modulu můžou pokračovat i po `ModuleLoadFinished` zpětném volání.</span><span class="sxs-lookup"><span data-stu-id="938a1-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="938a1-111">Neúspěšná hodnota HRESULT v `hrStatus` znamená selhání.</span><span class="sxs-lookup"><span data-stu-id="938a1-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="938a1-112">Úspěch HRESULT v v `hrStatus` znamená pouze to, že první část načtení modulu byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="938a1-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="938a1-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="938a1-113">Requirements</span></span>  
 <span data-ttu-id="938a1-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="938a1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="938a1-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="938a1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="938a1-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="938a1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="938a1-117">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="938a1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="938a1-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="938a1-118">See also</span></span>

- [<span data-ttu-id="938a1-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="938a1-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="938a1-120">ModuleLoadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="938a1-120">ModuleLoadStarted Method</span></span>](icorprofilercallback-moduleloadstarted-method.md)
