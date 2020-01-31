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
ms.openlocfilehash: 695a4386d9399a079df41f11f52a3185083784ed
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861382"
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="497d7-102">ICorProfilerModuleEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="497d7-102">ICorProfilerModuleEnum::Next Method</span></span>
<span data-ttu-id="497d7-103">Získá zadaný počet souvislých modulů ze sekvenční kolekce modulů počínaje aktuální pozicí čítače výčtu v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="497d7-103">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="497d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="497d7-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="497d7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="497d7-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="497d7-106">pro Počet modulů, které se mají načíst.</span><span class="sxs-lookup"><span data-stu-id="497d7-106">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="497d7-107">mimo Pole hodnot `ModuleID`, z nichž každý představuje načtený modul.</span><span class="sxs-lookup"><span data-stu-id="497d7-107">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="497d7-108">mimo Ukazatel na počet prvků, které jsou ve skutečnosti vráceny v poli `ids`.</span><span class="sxs-lookup"><span data-stu-id="497d7-108">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="497d7-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="497d7-109">Return Value</span></span>  
 <span data-ttu-id="497d7-110">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="497d7-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="497d7-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="497d7-111">HRESULT</span></span>|<span data-ttu-id="497d7-112">Popis</span><span class="sxs-lookup"><span data-stu-id="497d7-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="497d7-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="497d7-113">S_OK</span></span>|<span data-ttu-id="497d7-114">byly vráceny `celt` prvky.</span><span class="sxs-lookup"><span data-stu-id="497d7-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="497d7-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="497d7-115">S_FALSE</span></span>|<span data-ttu-id="497d7-116">Bylo vráceno méně než `celt` prvků, což naznačuje, že byl výčet dokončen.</span><span class="sxs-lookup"><span data-stu-id="497d7-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="497d7-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="497d7-117">Requirements</span></span>  
 <span data-ttu-id="497d7-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="497d7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="497d7-119">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="497d7-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="497d7-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="497d7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="497d7-121">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="497d7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="497d7-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="497d7-122">See also</span></span>

- [<span data-ttu-id="497d7-123">ICorProfilerModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="497d7-123">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="497d7-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="497d7-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
