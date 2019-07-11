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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67a680727e824cbe29b9e022e00d661e8694f153
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780571"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="aaebf-102">ICorProfilerInfo::GetInprocInspectionInterface – metoda</span><span class="sxs-lookup"><span data-stu-id="aaebf-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="aaebf-103">Získá objekt, který může být dotazována v rámci rozhraní "ICorDebugProcess".</span><span class="sxs-lookup"><span data-stu-id="aaebf-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="aaebf-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="aaebf-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaebf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aaebf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aaebf-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="aaebf-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="aaebf-107">[navýšení kapacity](/cpp/atl/iunknown) objekt, který je možné zadávat dotazy pro `ICorDebugProcess` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aaebf-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aaebf-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aaebf-108">Remarks</span></span>  
 <span data-ttu-id="aaebf-109">Common language runtime (CLR) ladění v rozhraní API nepodporuje omezené vnitroprocesové ladění v rozhraní .NET Framework verze 1.0.</span><span class="sxs-lookup"><span data-stu-id="aaebf-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="aaebf-110">Vnitroprocesové ladění povolit profiler použití kontroly části rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="aaebf-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="aaebf-111">V důsledku zpětné vazby od zákazníků vnitroprocesové ladění bylo odstraněno z rozhraní .NET Framework verze 2.0 a jsme nahradili sadou funkcí, které jsou více tato rozhraní API profilování.</span><span class="sxs-lookup"><span data-stu-id="aaebf-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaebf-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aaebf-112">Requirements</span></span>  
 <span data-ttu-id="aaebf-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aaebf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aaebf-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aaebf-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aaebf-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aaebf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aaebf-116">**Verze rozhraní .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="aaebf-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaebf-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aaebf-117">See also</span></span>

- [<span data-ttu-id="aaebf-118">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aaebf-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
