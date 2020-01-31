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
ms.openlocfilehash: 5c9258126c872bd501b4eebc4698b4dded402dfe
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863358"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="a530a-102">ICorProfilerInfo::GetInprocInspectionInterface – metoda</span><span class="sxs-lookup"><span data-stu-id="a530a-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="a530a-103">Získá objekt, na který lze zadat dotaz na rozhraní "ICorDebugProcess".</span><span class="sxs-lookup"><span data-stu-id="a530a-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="a530a-104">Tato metoda je zastaralá ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="a530a-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a530a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a530a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a530a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a530a-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="a530a-107">objekt [out](/cpp/atl/iunknown) , na který lze zadat dotaz na rozhraní `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="a530a-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a530a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a530a-108">Remarks</span></span>  
 <span data-ttu-id="a530a-109">Rozhraní API pro ladění modulu CLR (Common Language Runtime) podporuje omezené ladění v procesu .NET Framework verze 1,0.</span><span class="sxs-lookup"><span data-stu-id="a530a-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="a530a-110">Ladění v rámci procesu povolilo profiler pro použití kontrolních částí rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="a530a-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="a530a-111">V důsledku zpětné vazby od zákazníků se vnitroprocesové ladění odebralo z .NET Framework ve verzi 2,0 a nahrazuje se sadou funkcí, které jsou v souladu s rozhraním API profilování.</span><span class="sxs-lookup"><span data-stu-id="a530a-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a530a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a530a-112">Requirements</span></span>  
 <span data-ttu-id="a530a-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a530a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a530a-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a530a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a530a-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a530a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a530a-116">**Verze .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="a530a-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a530a-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a530a-117">See also</span></span>

- [<span data-ttu-id="a530a-118">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a530a-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
