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
ms.openlocfilehash: 08fbf49e6944de4934a9fe7a960405ee96a7d8e3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445935"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="ca0b5-102">ICorProfilerCallback::ModuleLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="ca0b5-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="ca0b5-103">Notifies the profiler that a module has finished loading.</span><span class="sxs-lookup"><span data-stu-id="ca0b5-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca0b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca0b5-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca0b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ca0b5-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="ca0b5-106">[in] The ID of the module that has finished loading.</span><span class="sxs-lookup"><span data-stu-id="ca0b5-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="ca0b5-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span><span class="sxs-lookup"><span data-stu-id="ca0b5-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca0b5-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ca0b5-108">Remarks</span></span>  
 <span data-ttu-id="ca0b5-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span><span class="sxs-lookup"><span data-stu-id="ca0b5-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="ca0b5-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span><span class="sxs-lookup"><span data-stu-id="ca0b5-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="ca0b5-111">A failure HRESULT in `hrStatus` indicates a failure.</span><span class="sxs-lookup"><span data-stu-id="ca0b5-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="ca0b5-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span><span class="sxs-lookup"><span data-stu-id="ca0b5-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca0b5-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ca0b5-113">Requirements</span></span>  
 <span data-ttu-id="ca0b5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca0b5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca0b5-115">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ca0b5-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ca0b5-116">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca0b5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca0b5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca0b5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca0b5-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca0b5-118">See also</span></span>

- [<span data-ttu-id="ca0b5-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca0b5-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="ca0b5-120">ModuleLoadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="ca0b5-120">ModuleLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
