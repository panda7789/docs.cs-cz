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
ms.openlocfilehash: 618be7482616ea155798973d02a90f32d46164db
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780270"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="19557-102">ICorProfilerInfo::BeginInprocDebugging – metoda</span><span class="sxs-lookup"><span data-stu-id="19557-102">ICorProfilerInfo::BeginInprocDebugging Method</span></span>
<span data-ttu-id="19557-103">Inicializuje podporu ladění v procesu.</span><span class="sxs-lookup"><span data-stu-id="19557-103">Initializes in-process debugging support.</span></span> <span data-ttu-id="19557-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="19557-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19557-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19557-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19557-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="19557-106">Parameters</span></span>  
 `fThisThreadOnly`  
 <span data-ttu-id="19557-107">[in] Nastavte tuto hodnotu na `true` inicializovat podporu ladění pro pouze aktuální vlákno, nastavte ho na `false` inicializovat podporu ladění pro všemi vlákny.</span><span class="sxs-lookup"><span data-stu-id="19557-107">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="19557-108">[out] Ukazatel na vrácené hodnoty, který identifikuje relace ladění.</span><span class="sxs-lookup"><span data-stu-id="19557-108">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19557-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="19557-109">Remarks</span></span>  
 <span data-ttu-id="19557-110">Ladění služby CLR nepodporuje omezené vnitroprocesové ladění v rozhraní .NET Framework verze 1.0 a 1.1.</span><span class="sxs-lookup"><span data-stu-id="19557-110">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="19557-111">Vnitroprocesové ladění povolit profiler použití kontroly části rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="19557-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="19557-112">Ale z důvodu zpětné vazby od zákazníků, vnitroprocesové ladění má byla odebrána z rozhraní .NET Framework verze 2.0 a jsme nahradili sadou funkcí, které jsou více tato rozhraní API profilování.</span><span class="sxs-lookup"><span data-stu-id="19557-112">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19557-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="19557-113">Requirements</span></span>  
 <span data-ttu-id="19557-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19557-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19557-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="19557-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="19557-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19557-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19557-117">**Verze rozhraní .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="19557-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19557-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19557-118">See also</span></span>

- [<span data-ttu-id="19557-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="19557-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
