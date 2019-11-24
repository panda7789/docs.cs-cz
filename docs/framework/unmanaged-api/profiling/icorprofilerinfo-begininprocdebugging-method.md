---
title: ICorProfilerInfo::BeginInprocDebugging – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.BeginInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type:
- apiref
ms.openlocfilehash: fffc028c7706c86e8384483cc92ebad90b292861
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447746"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="182a8-102">ICorProfilerInfo::BeginInprocDebugging – metoda</span><span class="sxs-lookup"><span data-stu-id="182a8-102">ICorProfilerInfo::BeginInprocDebugging Method</span></span>
<span data-ttu-id="182a8-103">Initializes in-process debugging support.</span><span class="sxs-lookup"><span data-stu-id="182a8-103">Initializes in-process debugging support.</span></span> <span data-ttu-id="182a8-104">This method is obsolete in the .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="182a8-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="182a8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="182a8-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="182a8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="182a8-106">Parameters</span></span>  
 `fThisThreadOnly`  
 <span data-ttu-id="182a8-107">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span><span class="sxs-lookup"><span data-stu-id="182a8-107">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="182a8-108">[out] The pointer to a returned value that identifies the debugging session.</span><span class="sxs-lookup"><span data-stu-id="182a8-108">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="182a8-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="182a8-109">Remarks</span></span>  
 <span data-ttu-id="182a8-110">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span><span class="sxs-lookup"><span data-stu-id="182a8-110">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="182a8-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span><span class="sxs-lookup"><span data-stu-id="182a8-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="182a8-112">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span><span class="sxs-lookup"><span data-stu-id="182a8-112">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="182a8-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="182a8-113">Requirements</span></span>  
 <span data-ttu-id="182a8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="182a8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="182a8-115">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="182a8-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="182a8-116">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="182a8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="182a8-117">**.NET Framework Version:** 1.0</span><span class="sxs-lookup"><span data-stu-id="182a8-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="182a8-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="182a8-118">See also</span></span>

- [<span data-ttu-id="182a8-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="182a8-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
