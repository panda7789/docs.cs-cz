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
ms.openlocfilehash: 40cb666c47c690dc930ec2cb7f6c89662464780e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445920"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="c0581-102">ICorProfilerCallback::ModuleUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="c0581-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>
<span data-ttu-id="c0581-103">Upozorní profileru, že se dokončilo uvolňování modulu.</span><span class="sxs-lookup"><span data-stu-id="c0581-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0581-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0581-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0581-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c0581-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="c0581-106">pro ID modulu, který byl uvolněn.</span><span class="sxs-lookup"><span data-stu-id="c0581-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="c0581-107">pro Hodnota HRESULT, která označuje, zda byl modul úspěšně uvolněn.</span><span class="sxs-lookup"><span data-stu-id="c0581-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0581-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c0581-108">Remarks</span></span>  
 <span data-ttu-id="c0581-109">Hodnota `moduleId` není platná pro požadavek na informace po návratu metody [ICorProfilerCallback:: moduleunloadstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c0581-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="c0581-110">Některé části uvolňování třídy mohou pokračovat po `ModuleUnloadFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="c0581-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="c0581-111">Selhání HRESULT v `hrStatus` označuje selhání.</span><span class="sxs-lookup"><span data-stu-id="c0581-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="c0581-112">Úspěšnost HRESULT v `hrStatus` však znamená, že první část uvolňování modulu byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="c0581-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0581-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c0581-113">Requirements</span></span>  
 <span data-ttu-id="c0581-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0581-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0581-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c0581-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c0581-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c0581-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0581-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0581-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0581-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0581-118">See also</span></span>

- [<span data-ttu-id="c0581-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c0581-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
