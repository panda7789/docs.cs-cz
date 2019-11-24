---
title: ICorProfilerInfo::SetILFunctionBody – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type:
- apiref
ms.openlocfilehash: da81bd3e255898543c94d4ac64c6afbf39b6bdba
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449883"
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a><span data-ttu-id="12d9c-102">ICorProfilerInfo::SetILFunctionBody – metoda</span><span class="sxs-lookup"><span data-stu-id="12d9c-102">ICorProfilerInfo::SetILFunctionBody Method</span></span>
<span data-ttu-id="12d9c-103">Replaces the body of the specified function in the specified module.</span><span class="sxs-lookup"><span data-stu-id="12d9c-103">Replaces the body of the specified function in the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12d9c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12d9c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12d9c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="12d9c-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="12d9c-106">[in] The ID of the module in which the function resides.</span><span class="sxs-lookup"><span data-stu-id="12d9c-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodid`  
 <span data-ttu-id="12d9c-107">[in] The token of the function for which to replace the body.</span><span class="sxs-lookup"><span data-stu-id="12d9c-107">[in] The token of the function for which to replace the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="12d9c-108">[in] The new header for the function.</span><span class="sxs-lookup"><span data-stu-id="12d9c-108">[in] The new header for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12d9c-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12d9c-109">Remarks</span></span>  
 <span data-ttu-id="12d9c-110">The `SetILFunctionBody` method replaces the relative virtual address of the function in the metadata so that it points to the new function body, and adjusts any internal data structures as required.</span><span class="sxs-lookup"><span data-stu-id="12d9c-110">The `SetILFunctionBody` method replaces the relative virtual address of the function in the metadata so that it points to the new function body, and adjusts any internal data structures as required.</span></span>  
  
 <span data-ttu-id="12d9c-111">The `SetILFunctionBody` method can be called on only those functions that have never been compiled by a just-in-time (JIT) compiler.</span><span class="sxs-lookup"><span data-stu-id="12d9c-111">The `SetILFunctionBody` method can be called on only those functions that have never been compiled by a just-in-time (JIT) compiler.</span></span>  
  
 <span data-ttu-id="12d9c-112">Use the [ICorProfilerInfo::GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) method to allocate space for the new method to ensure that the buffer is compatible.</span><span class="sxs-lookup"><span data-stu-id="12d9c-112">Use the [ICorProfilerInfo::GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) method to allocate space for the new method to ensure that the buffer is compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12d9c-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12d9c-113">Requirements</span></span>  
 <span data-ttu-id="12d9c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12d9c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12d9c-115">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="12d9c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="12d9c-116">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12d9c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12d9c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12d9c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12d9c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12d9c-118">See also</span></span>

- [<span data-ttu-id="12d9c-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12d9c-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
