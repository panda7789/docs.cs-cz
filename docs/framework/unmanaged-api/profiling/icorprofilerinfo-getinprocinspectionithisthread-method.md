---
title: ICorProfilerInfo::GetInprocInspectionIThisThread – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionIThisThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 24b7af4b44d51da06e9d65104f1b469ef1d83b8a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59219431"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="edbf8-102">ICorProfilerInfo::GetInprocInspectionIThisThread – metoda</span><span class="sxs-lookup"><span data-stu-id="edbf8-102">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>
<span data-ttu-id="edbf8-103">Získá objekt, který je možné zadávat dotazy pro icordebugthread – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="edbf8-103">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="edbf8-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="edbf8-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edbf8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="edbf8-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="edbf8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="edbf8-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="edbf8-107">[navýšení kapacity](/cpp/atl/iunknown) objekt, který může být dotázán na `ICorDebugThread` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="edbf8-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edbf8-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="edbf8-108">Remarks</span></span>  
 <span data-ttu-id="edbf8-109">Common language runtime (CLR) ladění služeb podporované omezené vnitroprocesové ladění v rozhraní .NET Framework verze 1.0.</span><span class="sxs-lookup"><span data-stu-id="edbf8-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="edbf8-110">Vnitroprocesové ladění povolit profiler použití kontroly části rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="edbf8-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="edbf8-111">V důsledku zpětné vazby od zákazníků vnitroprocesové ladění bylo odstraněno z rozhraní .NET Framework verze 2.0 a jsme nahradili sadou funkcí, které jsou více tato rozhraní API profilování.</span><span class="sxs-lookup"><span data-stu-id="edbf8-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edbf8-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="edbf8-112">Requirements</span></span>  
 <span data-ttu-id="edbf8-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edbf8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edbf8-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="edbf8-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="edbf8-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="edbf8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="edbf8-116">**Verze rozhraní .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="edbf8-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edbf8-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="edbf8-117">See also</span></span>

- [<span data-ttu-id="edbf8-118">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="edbf8-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
