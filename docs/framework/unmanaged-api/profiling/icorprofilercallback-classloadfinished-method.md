---
title: ICorProfilerCallback::ClassLoadFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type:
- apiref
ms.openlocfilehash: ef2c518f8f3f3069e93f06de89add1385cb4e45e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445119"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="e8154-102">ICorProfilerCallback::ClassLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="e8154-102">ICorProfilerCallback::ClassLoadFinished Method</span></span>
<span data-ttu-id="e8154-103">Notifies the profiler that a class has finished loading.</span><span class="sxs-lookup"><span data-stu-id="e8154-103">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8154-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8154-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8154-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8154-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="e8154-106">[in] Identifies the class that was loaded.</span><span class="sxs-lookup"><span data-stu-id="e8154-106">[in] Identifies the class that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="e8154-107">[in] An HRESULT that indicates whether the class loaded successfully.</span><span class="sxs-lookup"><span data-stu-id="e8154-107">[in] An HRESULT that indicates whether the class loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8154-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e8154-108">Remarks</span></span>  
 <span data-ttu-id="e8154-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span><span class="sxs-lookup"><span data-stu-id="e8154-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="e8154-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span><span class="sxs-lookup"><span data-stu-id="e8154-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="e8154-111">A failure HRESULT in `hrStatus` indicates a failure.</span><span class="sxs-lookup"><span data-stu-id="e8154-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="e8154-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span><span class="sxs-lookup"><span data-stu-id="e8154-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8154-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e8154-113">Requirements</span></span>  
 <span data-ttu-id="e8154-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8154-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8154-115">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e8154-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e8154-116">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8154-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8154-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8154-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8154-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8154-118">See also</span></span>

- [<span data-ttu-id="e8154-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e8154-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="e8154-120">ClassLoadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="e8154-120">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
