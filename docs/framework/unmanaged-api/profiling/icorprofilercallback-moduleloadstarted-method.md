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
ms.openlocfilehash: 88da5a968bf224dc5b6f45ee5d1d2e75386086f6
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866153"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="bcd6a-102">ICorProfilerCallback::ModuleLoadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="bcd6a-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>
<span data-ttu-id="bcd6a-103">Upozorní profileru, že je modul načítán.</span><span class="sxs-lookup"><span data-stu-id="bcd6a-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcd6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcd6a-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bcd6a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bcd6a-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="bcd6a-106">pro ID modulu, který se načítá.</span><span class="sxs-lookup"><span data-stu-id="bcd6a-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcd6a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bcd6a-107">Remarks</span></span>  
 <span data-ttu-id="bcd6a-108">Hodnota `moduleId` není platná pro požadavek na informace, dokud není volána metoda [ICorProfilerCallback:: ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bcd6a-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcd6a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bcd6a-109">Requirements</span></span>  
 <span data-ttu-id="bcd6a-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcd6a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcd6a-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bcd6a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bcd6a-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bcd6a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcd6a-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcd6a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcd6a-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bcd6a-114">See also</span></span>

- [<span data-ttu-id="bcd6a-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bcd6a-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
