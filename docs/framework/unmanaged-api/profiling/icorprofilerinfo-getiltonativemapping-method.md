---
title: ICorProfilerInfo::GetILToNativeMapping – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILToNativeMapping
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetILToNativeMapping method [.NET Framework profiling]
ms.assetid: 6a5431ef-22fb-4e53-bac5-703986297eb1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7bbf0e03fc69332f77f3ac34a399a96f638da3f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206717"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a><span data-ttu-id="6a320-102">ICorProfilerInfo::GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="6a320-102">ICorProfilerInfo::GetILToNativeMapping Method</span></span>
<span data-ttu-id="6a320-103">Získá mapování z Microsoft intermediate language (MSIL) kompenzuje do nativních posunů pro kód obsažený v zadané funkce.</span><span class="sxs-lookup"><span data-stu-id="6a320-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a320-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a320-104">Syntax</span></span>  
  
```  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a320-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a320-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="6a320-106">[in] ID funkce, která obsahuje kód.</span><span class="sxs-lookup"><span data-stu-id="6a320-106">[in] The ID of the function that contains the code.</span></span>  
  
 `cMap`  
 <span data-ttu-id="6a320-107">[in] Maximální velikost `map` pole.</span><span class="sxs-lookup"><span data-stu-id="6a320-107">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="6a320-108">[out] Celkový počet struktur cor_debug_il_to_native_map – k dispozici.</span><span class="sxs-lookup"><span data-stu-id="6a320-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="6a320-109">[out] Pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, z nichž každý určuje posunutí.</span><span class="sxs-lookup"><span data-stu-id="6a320-109">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="6a320-110">Po `GetILToNativeMapping` vrátí metoda `map` bude obsahovat některé nebo všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="6a320-110">After the `GetILToNativeMapping` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a320-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a320-111">Remarks</span></span>  
 <span data-ttu-id="6a320-112">`GetILToNativeMapping` Metoda vrátí pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="6a320-112">The `GetILToNativeMapping` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="6a320-113">Chcete-li sdělit, že určité rozsahy nativní pokyny odpovídají speciální oblasti kódu (například prologu), může mít položku v poli jeho `ilOffset` nastaveno na hodnotu [cordebugiltonativemappingtypes –](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) výčet.</span><span class="sxs-lookup"><span data-stu-id="6a320-113">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="6a320-114">Po `GetILToNativeMapping` vrátí, musíte ověřit, že `map` vyrovnávací paměť je dostatečně velký, aby obsahovala všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="6a320-114">After `GetILToNativeMapping` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="6a320-115">K tomuto účelu porovnat hodnotu `cMap` s hodnotou `pcMap` parametru.</span><span class="sxs-lookup"><span data-stu-id="6a320-115">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="6a320-116">Pokud `pcMap` hodnotu, pokud se násobí velikost `COR_DEBUG_IL_TO_NATIVE_MAP` strukturu, je větší než `cMap`, přidělte větší `map` vyrovnávací paměti, aktualizujte `cMap` nové, větší velikosti a volání `GetILToNativeMapping` znovu.</span><span class="sxs-lookup"><span data-stu-id="6a320-116">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping` again.</span></span>  
  
 <span data-ttu-id="6a320-117">Alternativně můžete nejprve volat `GetILToNativeMapping` s nulovou délkou `map` vyrovnávací paměť pro získání správné vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="6a320-117">Alternatively, you can first call `GetILToNativeMapping` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="6a320-118">Pak můžete nastavit velikost vyrovnávací paměti pro hodnotu vrácenou v `pcMap` a volat `GetILToNativeMapping` znovu.</span><span class="sxs-lookup"><span data-stu-id="6a320-118">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a320-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a320-119">Requirements</span></span>  
 <span data-ttu-id="6a320-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a320-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a320-121">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6a320-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6a320-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a320-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a320-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a320-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a320-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a320-124">See also</span></span>

- [<span data-ttu-id="6a320-125">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a320-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="6a320-126">GetILToNativeMapping2 – metoda</span><span class="sxs-lookup"><span data-stu-id="6a320-126">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)
- [<span data-ttu-id="6a320-127">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="6a320-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="6a320-128">Profilace</span><span class="sxs-lookup"><span data-stu-id="6a320-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
