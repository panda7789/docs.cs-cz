---
title: ICorProfilerCallback::ModuleLoadStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadStarted
helpviewer_keywords:
- ModuleLoadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadStarted method [.NET Framework profiling]
ms.assetid: 9cd2fe75-408a-400f-a6b1-9979624a2fe2
topic_type:
- apiref
ms.openlocfilehash: a04f72fff9a88c8689821131b08b35500c23b3d9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503351"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="f787e-102">ICorProfilerCallback::ModuleLoadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="f787e-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>
<span data-ttu-id="f787e-103">Upozorní profileru, že je modul načítán.</span><span class="sxs-lookup"><span data-stu-id="f787e-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f787e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f787e-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f787e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f787e-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="f787e-106">pro ID modulu, který se načítá.</span><span class="sxs-lookup"><span data-stu-id="f787e-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f787e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f787e-107">Remarks</span></span>  
 <span data-ttu-id="f787e-108">Hodnota `moduleId` není platná pro požadavek na informace, dokud není volána metoda [ICorProfilerCallback:: ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f787e-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f787e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f787e-109">Requirements</span></span>  
 <span data-ttu-id="f787e-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f787e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f787e-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f787e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f787e-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f787e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f787e-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f787e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f787e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f787e-114">See also</span></span>

- [<span data-ttu-id="f787e-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f787e-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
