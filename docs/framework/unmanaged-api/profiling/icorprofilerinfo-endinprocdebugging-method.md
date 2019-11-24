---
title: ICorProfilerInfo::EndInprocDebugging – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.EndInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::EndInprocDebugging
helpviewer_keywords:
- ICorProfilerInfo::EndInprocDebugging method [.NET Framework profiling]
- EndInprocDebugging method [.NET Framework profiling]
ms.assetid: 35bc1188-9767-4141-8038-60ea015b99ac
topic_type:
- apiref
ms.openlocfilehash: 09b1b81bde486db67acede99e0d67ff85cb01bae
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447765"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="46fc3-102">ICorProfilerInfo::EndInprocDebugging – metoda</span><span class="sxs-lookup"><span data-stu-id="46fc3-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="46fc3-103">Shuts down an in-process debugging session.</span><span class="sxs-lookup"><span data-stu-id="46fc3-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="46fc3-104">This method is obsolete in the .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="46fc3-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46fc3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46fc3-105">Syntax</span></span>  
  
```cpp  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46fc3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="46fc3-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="46fc3-107">[in] A value that identifies the debugging session.</span><span class="sxs-lookup"><span data-stu-id="46fc3-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="46fc3-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="46fc3-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46fc3-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="46fc3-109">Remarks</span></span>  
 <span data-ttu-id="46fc3-110">You must call [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span><span class="sxs-lookup"><span data-stu-id="46fc3-110">You must call [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="46fc3-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span><span class="sxs-lookup"><span data-stu-id="46fc3-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="46fc3-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span><span class="sxs-lookup"><span data-stu-id="46fc3-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="46fc3-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span><span class="sxs-lookup"><span data-stu-id="46fc3-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46fc3-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="46fc3-114">Requirements</span></span>  
 <span data-ttu-id="46fc3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46fc3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46fc3-116">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="46fc3-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="46fc3-117">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46fc3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46fc3-118">**.NET Framework Version:** 1.0</span><span class="sxs-lookup"><span data-stu-id="46fc3-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46fc3-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46fc3-119">See also</span></span>

- [<span data-ttu-id="46fc3-120">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46fc3-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
