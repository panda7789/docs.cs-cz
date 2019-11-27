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
ms.openlocfilehash: bcc324d0f5cd14e1de9f02c8e6844a5868b70e8b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438907"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="3458a-102">ICorProfilerInfo::GetInprocInspectionIThisThread – metoda</span><span class="sxs-lookup"><span data-stu-id="3458a-102">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>
<span data-ttu-id="3458a-103">Získá objekt, který lze dotazovat pro rozhraní ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="3458a-103">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="3458a-104">Tato metoda je zastaralá ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="3458a-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3458a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3458a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3458a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3458a-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="3458a-107">objekt [out](/cpp/atl/iunknown) , na který lze zadat dotaz na rozhraní `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3458a-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3458a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3458a-108">Remarks</span></span>  
 <span data-ttu-id="3458a-109">Služby ladění modulu CLR (Common Language Runtime) podporují omezené ladění v procesu .NET Framework verze 1,0.</span><span class="sxs-lookup"><span data-stu-id="3458a-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="3458a-110">Ladění v rámci procesu povolilo profiler pro použití kontrolních částí rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="3458a-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="3458a-111">V důsledku zpětné vazby od zákazníků se vnitroprocesové ladění odebralo z .NET Framework ve verzi 2,0 a nahrazuje se sadou funkcí, které jsou v souladu s rozhraním API profilování.</span><span class="sxs-lookup"><span data-stu-id="3458a-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3458a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3458a-112">Requirements</span></span>  
 <span data-ttu-id="3458a-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3458a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3458a-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3458a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3458a-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3458a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3458a-116">**Verze .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="3458a-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3458a-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3458a-117">See also</span></span>

- [<span data-ttu-id="3458a-118">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3458a-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
