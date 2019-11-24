---
title: ICorProfilerCallback::AssemblyLoadFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
ms.openlocfilehash: 33b72c8d089e5b335069fe465987086dfa1243bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445167"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="7f06b-102">ICorProfilerCallback::AssemblyLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="7f06b-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="7f06b-103">Notifies the profiler that an assembly has finished loading.</span><span class="sxs-lookup"><span data-stu-id="7f06b-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f06b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f06b-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f06b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f06b-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="7f06b-106">[in] Identifies the assembly that was loaded.</span><span class="sxs-lookup"><span data-stu-id="7f06b-106">[in] Identifies the assembly that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="7f06b-107">[in] An HRESULT that indicates whether the assembly finished loading successfully.</span><span class="sxs-lookup"><span data-stu-id="7f06b-107">[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f06b-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f06b-108">Remarks</span></span>  
 <span data-ttu-id="7f06b-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span><span class="sxs-lookup"><span data-stu-id="7f06b-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="7f06b-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span><span class="sxs-lookup"><span data-stu-id="7f06b-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="7f06b-111">A failure HRESULT in `hrStatus` indicates a failure.</span><span class="sxs-lookup"><span data-stu-id="7f06b-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="7f06b-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span><span class="sxs-lookup"><span data-stu-id="7f06b-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f06b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f06b-113">Requirements</span></span>  
 <span data-ttu-id="7f06b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f06b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f06b-115">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7f06b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7f06b-116">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f06b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f06b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f06b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f06b-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f06b-118">See also</span></span>

- [<span data-ttu-id="7f06b-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f06b-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
