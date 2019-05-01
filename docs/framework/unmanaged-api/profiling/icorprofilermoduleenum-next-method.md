---
title: ICorProfilerModuleEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Next
helpviewer_keywords:
- ICorProfilerModuleEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: a3cea59d-7622-4323-897a-0a464c40f77f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57d8279ba9733e6a381d445d50df56b415353a16
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000451"
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="bb985-102">ICorProfilerModuleEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="bb985-102">ICorProfilerModuleEnum::Next Method</span></span>
<span data-ttu-id="bb985-103">Získá zadaný počet souvislých moduly ze sekvenčního kolekce modulů, od aktuální pozice čítače výčtu v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="bb985-103">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb985-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb985-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb985-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb985-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="bb985-106">[in] Počet modulů pro načtení.</span><span class="sxs-lookup"><span data-stu-id="bb985-106">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="bb985-107">[out] Pole `ModuleID` hodnot, z nichž každý představuje načíst modul.</span><span class="sxs-lookup"><span data-stu-id="bb985-107">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="bb985-108">[out] Ukazatel na počet skutečně vrácených v prvků `ids` pole.</span><span class="sxs-lookup"><span data-stu-id="bb985-108">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb985-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bb985-109">Return Value</span></span>  
 <span data-ttu-id="bb985-110">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="bb985-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="bb985-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb985-111">HRESULT</span></span>|<span data-ttu-id="bb985-112">Popis</span><span class="sxs-lookup"><span data-stu-id="bb985-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bb985-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="bb985-113">S_OK</span></span>|<span data-ttu-id="bb985-114">`celt` elementy byly vráceny.</span><span class="sxs-lookup"><span data-stu-id="bb985-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="bb985-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="bb985-115">S_FALSE</span></span>|<span data-ttu-id="bb985-116">Méně než `celt` prvky byly vráceny, což znamená, že dokončení výčtu.</span><span class="sxs-lookup"><span data-stu-id="bb985-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bb985-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb985-117">Requirements</span></span>  
 <span data-ttu-id="bb985-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb985-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb985-119">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bb985-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bb985-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb985-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb985-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb985-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb985-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb985-122">See also</span></span>

- [<span data-ttu-id="bb985-123">ICorProfilerModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb985-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="bb985-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="bb985-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
