---
title: ICorProfilerInfo4::GetILToNativeMapping2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetILToNativeMapping2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2
helpviewer_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2 method [.NET Framework profiling]
- GetILToNativeMapping2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 756c1c25-08a7-4060-9798-dbeaa2f3bee5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ad83c376816c2203cd78a83b8664fa90b0e109fd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780831"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a><span data-ttu-id="4c1bf-102">ICorProfilerInfo4::GetILToNativeMapping2 – metoda</span><span class="sxs-lookup"><span data-stu-id="4c1bf-102">ICorProfilerInfo4::GetILToNativeMapping2 Method</span></span>
<span data-ttu-id="4c1bf-103">Získá mapování z Microsoft intermediate language (MSIL) kompenzuje do nativních posunů pro kód obsažený ve verzi překompilován JIT zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="4c1bf-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c1bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c1bf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c1bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c1bf-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="4c1bf-106">[in] ID funkce, která obsahuje kód.</span><span class="sxs-lookup"><span data-stu-id="4c1bf-106">[in] The ID of the function that contains the code.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="4c1bf-107">[in] Identita funkce překompilován JIT.</span><span class="sxs-lookup"><span data-stu-id="4c1bf-107">[in] The identity of the JIT-recompiled function.</span></span> <span data-ttu-id="4c1bf-108">Identita musí být nula v rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="4c1bf-108">The identity must be zero in the .NET Framework 4.5.</span></span>  
  
 `cMap`  
 <span data-ttu-id="4c1bf-109">[in] Maximální velikost `map` pole.</span><span class="sxs-lookup"><span data-stu-id="4c1bf-109">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="4c1bf-110">[out] Celkový počet struktur cor_debug_il_to_native_map – k dispozici.</span><span class="sxs-lookup"><span data-stu-id="4c1bf-110">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="4c1bf-111">[out] Pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, z nichž každý určuje posunutí.</span><span class="sxs-lookup"><span data-stu-id="4c1bf-111">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="4c1bf-112">Po `GetILToNativeMapping2` vrátí metoda `map` bude obsahovat některé nebo všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="4c1bf-112">After the `GetILToNativeMapping2` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c1bf-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4c1bf-113">Remarks</span></span>  
 <span data-ttu-id="4c1bf-114">`GetILToNativeMapping2` se podobá [icorprofilerinfo::getiltonativemapping –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) metody, s tím rozdílem, že bude možné profiler k určení ID překompilovanou funkce v budoucích verzí.</span><span class="sxs-lookup"><span data-stu-id="4c1bf-114">`GetILToNativeMapping2` is similar to the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method, except that it will allow the profiler to specify the ID of the recompiled function in future releases.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c1bf-115">[Icorprofilerfunctioncontrol::setilinstrumentedcodemap –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) metoda není implementovaná v rozhraní .NET Framework 4.5, funkce, které byly překompilován JIT nemůže mít IL na nativní mapování, která se liší od původně zkompilované funkce.</span><span class="sxs-lookup"><span data-stu-id="4c1bf-115">The [ICorProfilerFunctionControl::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) method is not implemented in the .NET Framework 4.5, so functions that have been JIT-recompiled cannot have an IL-to-native mapping that differs from the originally compiled function.</span></span> <span data-ttu-id="4c1bf-116">V důsledku toho `GetILToNativeMapping2` nelze volat s nenulovou hodnotu ID překompilován JIT v rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="4c1bf-116">As such, `GetILToNativeMapping2` cannot be called with a nonzero JIT-recompiled ID in the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="4c1bf-117">`GetILToNativeMapping2` Metoda vrátí pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="4c1bf-117">The `GetILToNativeMapping2` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="4c1bf-118">Chcete-li sdělit, že určité rozsahy nativní pokyny odpovídají speciální oblasti kódu (například prologu), může mít položku v poli jeho `ilOffset` nastaveno na hodnotu [cordebugiltonativemappingtypes –](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) výčet.</span><span class="sxs-lookup"><span data-stu-id="4c1bf-118">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="4c1bf-119">Po `GetILToNativeMapping2` vrátí, musíte ověřit, že `map` vyrovnávací paměť je dostatečně velký, aby obsahovala všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="4c1bf-119">After `GetILToNativeMapping2` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="4c1bf-120">K tomuto účelu porovnat hodnotu `cMap` s hodnotou `pcMap` parametru.</span><span class="sxs-lookup"><span data-stu-id="4c1bf-120">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="4c1bf-121">Pokud `pcMap` hodnotu, pokud se násobí velikost `COR_DEBUG_IL_TO_NATIVE_MAP` strukturu, je větší než `cMap`, přidělte větší `map` vyrovnávací paměti, aktualizujte `cMap` nové, větší velikosti a volání `GetILToNativeMapping2` znovu.</span><span class="sxs-lookup"><span data-stu-id="4c1bf-121">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping2` again.</span></span>  
  
 <span data-ttu-id="4c1bf-122">Alternativně můžete nejprve volat `GetILToNativeMapping2` s nulovou délkou `map` vyrovnávací paměť pro získání správné vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="4c1bf-122">Alternatively, you can first call `GetILToNativeMapping2` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="4c1bf-123">Pak můžete nastavit velikost vyrovnávací paměti pro hodnotu vrácenou v `pcMap` a volat `GetILToNativeMapping2` znovu.</span><span class="sxs-lookup"><span data-stu-id="4c1bf-123">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c1bf-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4c1bf-124">Requirements</span></span>  
 <span data-ttu-id="4c1bf-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c1bf-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c1bf-126">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4c1bf-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4c1bf-127">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c1bf-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c1bf-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c1bf-128">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c1bf-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c1bf-129">See also</span></span>

- [<span data-ttu-id="4c1bf-130">GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="4c1bf-130">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="4c1bf-131">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c1bf-131">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="4c1bf-132">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="4c1bf-132">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="4c1bf-133">Profilace</span><span class="sxs-lookup"><span data-stu-id="4c1bf-133">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
