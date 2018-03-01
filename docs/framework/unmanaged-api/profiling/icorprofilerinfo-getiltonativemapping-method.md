---
title: "ICorProfilerInfo::GetILToNativeMapping – metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 89ccfcbf69a0d3907ec244d7a214d6f4a5766767
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a><span data-ttu-id="5ec46-102">ICorProfilerInfo::GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="5ec46-102">ICorProfilerInfo::GetILToNativeMapping Method</span></span>
<span data-ttu-id="5ec46-103">Získá mapu od společnosti Microsoft (MSIL intermediate language) posune do nativní posunutí pro kód obsažené v zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="5ec46-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ec46-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ec46-104">Syntax</span></span>  
  
```  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5ec46-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5ec46-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="5ec46-106">[v] ID funkce, která obsahuje kód.</span><span class="sxs-lookup"><span data-stu-id="5ec46-106">[in] The ID of the function that contains the code.</span></span>  
  
 `cMap`  
 <span data-ttu-id="5ec46-107">[v] Maximální velikost `map` pole.</span><span class="sxs-lookup"><span data-stu-id="5ec46-107">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="5ec46-108">[out] Celkový počet dostupných cor_debug_il_to_native_map – struktury.</span><span class="sxs-lookup"><span data-stu-id="5ec46-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="5ec46-109">[out] Pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, z nichž každý určuje posunutí.</span><span class="sxs-lookup"><span data-stu-id="5ec46-109">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="5ec46-110">Po `GetILToNativeMapping` metoda vrátí `map` bude obsahovat některé nebo všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="5ec46-110">After the `GetILToNativeMapping` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ec46-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5ec46-111">Remarks</span></span>  
 <span data-ttu-id="5ec46-112">`GetILToNativeMapping` Metoda vrátí pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="5ec46-112">The `GetILToNativeMapping` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="5ec46-113">Chcete-li sdělit, že určitých rozsahů nativní pokyny odpovídají speciální oblasti kódu (například prologu), může mít položku v poli jeho `ilOffset` pole nastaveno na hodnotu [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) výčet.</span><span class="sxs-lookup"><span data-stu-id="5ec46-113">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="5ec46-114">Po `GetILToNativeMapping` vrátí, musíte ověřit, že `map` vyrovnávací paměť byla dostatečně velký pro obsahovat všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="5ec46-114">After `GetILToNativeMapping` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="5ec46-115">K tomuto účelu porovnat hodnotu `cMap` s hodnotou `pcMap` parametr.</span><span class="sxs-lookup"><span data-stu-id="5ec46-115">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="5ec46-116">Pokud `pcMap` hodnotu, pokud se násobí velikostí `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, je větší než `cMap`, přidělit větší `map` vyrovnávací paměti, aktualizujte `cMap` s novou, větší velikost a volání `GetILToNativeMapping` znovu.</span><span class="sxs-lookup"><span data-stu-id="5ec46-116">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping` again.</span></span>  
  
 <span data-ttu-id="5ec46-117">Alternativně můžete nejdřív volat `GetILToNativeMapping` s nulovou délkou `map` vyrovnávací paměti se získat velikost správné vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="5ec46-117">Alternatively, you can first call `GetILToNativeMapping` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="5ec46-118">Velikost vyrovnávací paměti pak můžete nastavit na hodnotu, vrátí se v `pcMap` a volání `GetILToNativeMapping` znovu.</span><span class="sxs-lookup"><span data-stu-id="5ec46-118">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ec46-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5ec46-119">Requirements</span></span>  
 <span data-ttu-id="5ec46-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ec46-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ec46-121">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5ec46-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5ec46-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ec46-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ec46-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ec46-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ec46-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ec46-124">See Also</span></span>  
 [<span data-ttu-id="5ec46-125">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5ec46-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="5ec46-126">GetILToNativeMapping2 – metoda</span><span class="sxs-lookup"><span data-stu-id="5ec46-126">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)  
 [<span data-ttu-id="5ec46-127">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="5ec46-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="5ec46-128">Profilace</span><span class="sxs-lookup"><span data-stu-id="5ec46-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
