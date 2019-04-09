---
title: ICorProfilerFunctionEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Next
helpviewer_keywords:
- ICorProfilerFunctionEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 5ed4aa83-ce56-4b9f-9237-5da7587787fe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 62e70a2fe421651aac9a4921ca885c53c864c4f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101800"
---
# <a name="icorprofilerfunctionenumnext-method"></a><span data-ttu-id="7c109-102">ICorProfilerFunctionEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="7c109-102">ICorProfilerFunctionEnum::Next Method</span></span>
<span data-ttu-id="7c109-103">Získá zadaný počet souvislých funkce z sekvenční kolekce funkcí, od aktuální pozice čítače výčtu v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="7c109-103">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c109-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c109-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    COR_PRF_FUNCTION ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c109-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c109-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7c109-106">[in] Počet funkcí k načtení.</span><span class="sxs-lookup"><span data-stu-id="7c109-106">[in] The number of functions to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="7c109-107">[out] Pole `COR_PRF_FUNCTION` hodnot, z nichž každý představuje načtený funkce.</span><span class="sxs-lookup"><span data-stu-id="7c109-107">[out] An array of `COR_PRF_FUNCTION` values, each of which represents a retrieved function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="7c109-108">[out] Ukazatel na počet skutečně vrácených v funkcí, které `ids` pole.</span><span class="sxs-lookup"><span data-stu-id="7c109-108">[out] A pointer to the number of functions actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c109-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7c109-109">Return Value</span></span>  
 <span data-ttu-id="7c109-110">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="7c109-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7c109-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7c109-111">HRESULT</span></span>|<span data-ttu-id="7c109-112">Popis</span><span class="sxs-lookup"><span data-stu-id="7c109-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7c109-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="7c109-113">S_OK</span></span>|`celt` <span data-ttu-id="7c109-114">elementy byly vráceny.</span><span class="sxs-lookup"><span data-stu-id="7c109-114">elements were returned.</span></span>|  
|<span data-ttu-id="7c109-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="7c109-115">S_FALSE</span></span>|<span data-ttu-id="7c109-116">Méně než `celt` prvky byly vráceny, což znamená, že dokončení výčtu.</span><span class="sxs-lookup"><span data-stu-id="7c109-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7c109-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c109-117">Requirements</span></span>  
 <span data-ttu-id="7c109-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c109-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c109-119">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7c109-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7c109-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c109-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7c109-121">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7c109-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7c109-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c109-122">See also</span></span>

- [<span data-ttu-id="7c109-123">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c109-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="7c109-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="7c109-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
