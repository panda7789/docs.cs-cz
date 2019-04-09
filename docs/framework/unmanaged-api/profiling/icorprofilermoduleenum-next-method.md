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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077144"
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="0adeb-102">ICorProfilerModuleEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="0adeb-102">ICorProfilerModuleEnum::Next Method</span></span>
<span data-ttu-id="0adeb-103">Získá zadaný počet souvislých moduly ze sekvenčního kolekce modulů, od aktuální pozice čítače výčtu v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="0adeb-103">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0adeb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0adeb-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0adeb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0adeb-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="0adeb-106">[in] Počet modulů pro načtení.</span><span class="sxs-lookup"><span data-stu-id="0adeb-106">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="0adeb-107">[out] Pole `ModuleID` hodnot, z nichž každý představuje načíst modul.</span><span class="sxs-lookup"><span data-stu-id="0adeb-107">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="0adeb-108">[out] Ukazatel na počet skutečně vrácených v prvků `ids` pole.</span><span class="sxs-lookup"><span data-stu-id="0adeb-108">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0adeb-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0adeb-109">Return Value</span></span>  
 <span data-ttu-id="0adeb-110">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="0adeb-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0adeb-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0adeb-111">HRESULT</span></span>|<span data-ttu-id="0adeb-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0adeb-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0adeb-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="0adeb-113">S_OK</span></span>|`celt` <span data-ttu-id="0adeb-114">elementy byly vráceny.</span><span class="sxs-lookup"><span data-stu-id="0adeb-114">elements were returned.</span></span>|  
|<span data-ttu-id="0adeb-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0adeb-115">S_FALSE</span></span>|<span data-ttu-id="0adeb-116">Méně než `celt` prvky byly vráceny, což znamená, že dokončení výčtu.</span><span class="sxs-lookup"><span data-stu-id="0adeb-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0adeb-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0adeb-117">Requirements</span></span>  
 <span data-ttu-id="0adeb-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0adeb-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0adeb-119">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0adeb-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0adeb-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0adeb-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0adeb-121">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0adeb-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0adeb-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0adeb-122">See also</span></span>

- [<span data-ttu-id="0adeb-123">ICorProfilerModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0adeb-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="0adeb-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="0adeb-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
