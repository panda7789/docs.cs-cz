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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 330a159e056018d702eec7e4fef80c3d8e041212
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54630798"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="e8527-102">ICorProfilerInfo::BeginInprocDebugging – metoda</span><span class="sxs-lookup"><span data-stu-id="e8527-102">ICorProfilerInfo::BeginInprocDebugging Method</span></span>
<span data-ttu-id="e8527-103">Inicializuje podporu ladění v procesu.</span><span class="sxs-lookup"><span data-stu-id="e8527-103">Initializes in-process debugging support.</span></span> <span data-ttu-id="e8527-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="e8527-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8527-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8527-105">Syntax</span></span>  
  
```  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8527-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8527-106">Parameters</span></span>  
 `fThisThreadOnly`  
 <span data-ttu-id="e8527-107">[in] Nastavte tuto hodnotu na `true` inicializovat podporu ladění pro pouze aktuální vlákno, nastavte ho na `false` inicializovat podporu ladění pro všemi vlákny.</span><span class="sxs-lookup"><span data-stu-id="e8527-107">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="e8527-108">[out] Ukazatel na vrácené hodnoty, který identifikuje relace ladění.</span><span class="sxs-lookup"><span data-stu-id="e8527-108">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8527-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e8527-109">Remarks</span></span>  
 <span data-ttu-id="e8527-110">Ladění služby CLR nepodporuje omezené vnitroprocesové ladění v rozhraní .NET Framework verze 1.0 a 1.1.</span><span class="sxs-lookup"><span data-stu-id="e8527-110">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="e8527-111">Vnitroprocesové ladění povolit profiler použití kontroly části rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="e8527-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="e8527-112">Ale z důvodu zpětné vazby od zákazníků, vnitroprocesové ladění má byla odebrána z rozhraní .NET Framework verze 2.0 a jsme nahradili sadou funkcí, které jsou více tato rozhraní API profilování.</span><span class="sxs-lookup"><span data-stu-id="e8527-112">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8527-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e8527-113">Requirements</span></span>  
 <span data-ttu-id="e8527-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8527-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8527-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e8527-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e8527-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8527-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8527-117">**Verze rozhraní .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="e8527-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8527-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8527-118">See also</span></span>
- [<span data-ttu-id="e8527-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e8527-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
