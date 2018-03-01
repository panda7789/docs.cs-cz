---
title: "ICorProfilerInfo4::GetILToNativeMapping2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2d5ce076ad66214f786f7e221a0443edf7986c5d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a><span data-ttu-id="02cd4-102">ICorProfilerInfo4::GetILToNativeMapping2 – metoda</span><span class="sxs-lookup"><span data-stu-id="02cd4-102">ICorProfilerInfo4::GetILToNativeMapping2 Method</span></span>
<span data-ttu-id="02cd4-103">Získá mapu od společnosti Microsoft (MSIL intermediate language) posune do nativní posunutí pro kód obsažené ve verzi překompilovat JIT zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="02cd4-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02cd4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02cd4-104">Syntax</span></span>  
  
```  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="02cd4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="02cd4-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="02cd4-106">[v] ID funkce, která obsahuje kód.</span><span class="sxs-lookup"><span data-stu-id="02cd4-106">[in] The ID of the function that contains the code.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="02cd4-107">[v] Identita překompilovat JIT funkce.</span><span class="sxs-lookup"><span data-stu-id="02cd4-107">[in] The identity of the JIT-recompiled function.</span></span> <span data-ttu-id="02cd4-108">Identita musí být nula v [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="02cd4-108">The identity must be zero in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
 `cMap`  
 <span data-ttu-id="02cd4-109">[v] Maximální velikost `map` pole.</span><span class="sxs-lookup"><span data-stu-id="02cd4-109">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="02cd4-110">[out] Celkový počet dostupných cor_debug_il_to_native_map – struktury.</span><span class="sxs-lookup"><span data-stu-id="02cd4-110">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="02cd4-111">[out] Pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, z nichž každý určuje posunutí.</span><span class="sxs-lookup"><span data-stu-id="02cd4-111">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="02cd4-112">Po `GetILToNativeMapping2` metoda vrátí `map` bude obsahovat některé nebo všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="02cd4-112">After the `GetILToNativeMapping2` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02cd4-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="02cd4-113">Remarks</span></span>  
 <span data-ttu-id="02cd4-114">`GetILToNativeMapping2`je podobná [icorprofilerinfo::getiltonativemapping –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) metoda, s tím rozdílem, že bude možné profileru zadat ID Rekompilované funkce v budoucnosti uvolní.</span><span class="sxs-lookup"><span data-stu-id="02cd4-114">`GetILToNativeMapping2` is similar to the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method, except that it will allow the profiler to specify the ID of the recompiled function in future releases.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02cd4-115">[Icorprofilerfunctioncontrol::setilinstrumentedcodemap –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) metoda není implementována v [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], takže funkce, které byly překompilovat JIT nemůže mít IL nativní mapování, která se liší od původně kompilované funkce.</span><span class="sxs-lookup"><span data-stu-id="02cd4-115">The [ICorProfilerFunctionControl::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) method is not implemented in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], so functions that have been JIT-recompiled cannot have an IL-to-native mapping that differs from the originally compiled function.</span></span> <span data-ttu-id="02cd4-116">Jako takový `GetILToNativeMapping2` nejde volat s nenulovou překompilovat JIT ID v [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="02cd4-116">As such, `GetILToNativeMapping2` cannot be called with a nonzero JIT-recompiled ID in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
 <span data-ttu-id="02cd4-117">`GetILToNativeMapping2` Metoda vrátí pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="02cd4-117">The `GetILToNativeMapping2` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="02cd4-118">Chcete-li sdělit, že určitých rozsahů nativní pokyny odpovídají speciální oblasti kódu (například prologu), může mít položku v poli jeho `ilOffset` pole nastaveno na hodnotu [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) výčet.</span><span class="sxs-lookup"><span data-stu-id="02cd4-118">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="02cd4-119">Po `GetILToNativeMapping2` vrátí, musíte ověřit, že `map` vyrovnávací paměť byla dostatečně velký pro obsahovat všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="02cd4-119">After `GetILToNativeMapping2` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="02cd4-120">K tomuto účelu porovnat hodnotu `cMap` s hodnotou `pcMap` parametr.</span><span class="sxs-lookup"><span data-stu-id="02cd4-120">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="02cd4-121">Pokud `pcMap` hodnotu, pokud se násobí velikostí `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, je větší než `cMap`, přidělit větší `map` vyrovnávací paměti, aktualizujte `cMap` s novou, větší velikost a volání `GetILToNativeMapping2` znovu.</span><span class="sxs-lookup"><span data-stu-id="02cd4-121">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping2` again.</span></span>  
  
 <span data-ttu-id="02cd4-122">Alternativně můžete nejdřív volat `GetILToNativeMapping2` s nulovou délkou `map` vyrovnávací paměti se získat velikost správné vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="02cd4-122">Alternatively, you can first call `GetILToNativeMapping2` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="02cd4-123">Velikost vyrovnávací paměti pak můžete nastavit na hodnotu, vrátí se v `pcMap` a volání `GetILToNativeMapping2` znovu.</span><span class="sxs-lookup"><span data-stu-id="02cd4-123">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02cd4-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="02cd4-124">Requirements</span></span>  
 <span data-ttu-id="02cd4-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02cd4-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02cd4-126">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="02cd4-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="02cd4-127">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02cd4-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02cd4-128">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02cd4-128">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02cd4-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="02cd4-129">See Also</span></span>  
 [<span data-ttu-id="02cd4-130">GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="02cd4-130">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)  
 [<span data-ttu-id="02cd4-131">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="02cd4-131">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="02cd4-132">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="02cd4-132">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="02cd4-133">Profilace</span><span class="sxs-lookup"><span data-stu-id="02cd4-133">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
