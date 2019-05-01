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
ms.openlocfilehash: 456dd8aedf11b1b27ee4926988fc615ebb7a76d8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991819"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="d57cf-102">ICorProfilerInfo::GetInprocInspectionInterface – metoda</span><span class="sxs-lookup"><span data-stu-id="d57cf-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="d57cf-103">Získá objekt, který může být dotazována v rámci rozhraní "ICorDebugProcess".</span><span class="sxs-lookup"><span data-stu-id="d57cf-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="d57cf-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="d57cf-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d57cf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d57cf-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d57cf-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d57cf-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="d57cf-107">[navýšení kapacity](/cpp/atl/iunknown) objekt, který je možné zadávat dotazy pro `ICorDebugProcess` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d57cf-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d57cf-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d57cf-108">Remarks</span></span>  
 <span data-ttu-id="d57cf-109">Common language runtime (CLR) ladění v rozhraní API nepodporuje omezené vnitroprocesové ladění v rozhraní .NET Framework verze 1.0.</span><span class="sxs-lookup"><span data-stu-id="d57cf-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="d57cf-110">Vnitroprocesové ladění povolit profiler použití kontroly části rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="d57cf-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="d57cf-111">V důsledku zpětné vazby od zákazníků vnitroprocesové ladění bylo odstraněno z rozhraní .NET Framework verze 2.0 a jsme nahradili sadou funkcí, které jsou více tato rozhraní API profilování.</span><span class="sxs-lookup"><span data-stu-id="d57cf-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d57cf-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d57cf-112">Requirements</span></span>  
 <span data-ttu-id="d57cf-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d57cf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d57cf-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d57cf-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d57cf-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d57cf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d57cf-116">**Verze rozhraní .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="d57cf-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d57cf-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d57cf-117">See also</span></span>

- [<span data-ttu-id="d57cf-118">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d57cf-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
