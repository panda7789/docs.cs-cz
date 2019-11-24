---
title: ICorProfilerInfo::GetInprocInspectionInterface – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionInterface
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionInterface
helpviewer_keywords:
- GetInprocInspectionInterface method [.NET Framework profiling]
- ICorProfilerInfo::GetInprocInspectionInterface method [.NET Framework profiling]
ms.assetid: 22a92d1d-8849-4af6-8304-ecc53dd1d289
topic_type:
- apiref
ms.openlocfilehash: d3fcd859fb11f6a0c660751f16fa175e19e9d03b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439004"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="2cf74-102">ICorProfilerInfo::GetInprocInspectionInterface – metoda</span><span class="sxs-lookup"><span data-stu-id="2cf74-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="2cf74-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span><span class="sxs-lookup"><span data-stu-id="2cf74-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="2cf74-104">This method is obsolete in the .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="2cf74-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cf74-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cf74-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2cf74-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2cf74-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="2cf74-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span><span class="sxs-lookup"><span data-stu-id="2cf74-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cf74-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2cf74-108">Remarks</span></span>  
 <span data-ttu-id="2cf74-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span><span class="sxs-lookup"><span data-stu-id="2cf74-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="2cf74-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span><span class="sxs-lookup"><span data-stu-id="2cf74-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="2cf74-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span><span class="sxs-lookup"><span data-stu-id="2cf74-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cf74-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2cf74-112">Requirements</span></span>  
 <span data-ttu-id="2cf74-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cf74-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cf74-114">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2cf74-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2cf74-115">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2cf74-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2cf74-116">**.NET Framework Version:** 1.0</span><span class="sxs-lookup"><span data-stu-id="2cf74-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cf74-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2cf74-117">See also</span></span>

- [<span data-ttu-id="2cf74-118">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2cf74-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
