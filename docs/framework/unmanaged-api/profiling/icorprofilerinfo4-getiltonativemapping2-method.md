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
ms.openlocfilehash: 4fccee3b94efd65312206afb22c87f30609f9e6b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868457"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a><span data-ttu-id="772da-102">ICorProfilerInfo4::GetILToNativeMapping2 – metoda</span><span class="sxs-lookup"><span data-stu-id="772da-102">ICorProfilerInfo4::GetILToNativeMapping2 Method</span></span>
<span data-ttu-id="772da-103">Získá mapu z posunu od jazyka MSIL (Microsoft Intermediate Language) k nativním posunům pro kód obsažený v překompilované verzi zadané funkce JIT.</span><span class="sxs-lookup"><span data-stu-id="772da-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="772da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="772da-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="772da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="772da-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="772da-106">pro ID funkce, která obsahuje kód.</span><span class="sxs-lookup"><span data-stu-id="772da-106">[in] The ID of the function that contains the code.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="772da-107">pro Identita funkce Rekompilované JIT.</span><span class="sxs-lookup"><span data-stu-id="772da-107">[in] The identity of the JIT-recompiled function.</span></span> <span data-ttu-id="772da-108">V .NET Framework 4,5 musí být identita nula.</span><span class="sxs-lookup"><span data-stu-id="772da-108">The identity must be zero in the .NET Framework 4.5.</span></span>  
  
 `cMap`  
 <span data-ttu-id="772da-109">pro Maximální velikost `map` pole</span><span class="sxs-lookup"><span data-stu-id="772da-109">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="772da-110">mimo Celkový počet dostupných COR_DEBUG_IL_TO_NATIVE_MAP struktur.</span><span class="sxs-lookup"><span data-stu-id="772da-110">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="772da-111">mimo Pole struktur `COR_DEBUG_IL_TO_NATIVE_MAP`, z nichž každý Určuje posun.</span><span class="sxs-lookup"><span data-stu-id="772da-111">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="772da-112">Po návratu metody `GetILToNativeMapping2` bude `map` obsahovat některé nebo všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="772da-112">After the `GetILToNativeMapping2` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="772da-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="772da-113">Remarks</span></span>  
 <span data-ttu-id="772da-114">`GetILToNativeMapping2` je podobná metodě [ICorProfilerInfo:: GetILToNativeMapping –](icorprofilerinfo-getiltonativemapping-method.md) s tím rozdílem, že umožňuje profileru v budoucích verzích určit ID Rekompilované funkce.</span><span class="sxs-lookup"><span data-stu-id="772da-114">`GetILToNativeMapping2` is similar to the [ICorProfilerInfo::GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) method, except that it will allow the profiler to specify the ID of the recompiled function in future releases.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="772da-115">Metoda [ICorProfilerFunctionControl:: SetILInstrumentedCodeMap –](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) není implementována v .NET Framework 4,5, takže funkce, které byly rekompilovány JIT, nemohou mít mapování Il-to-Native, které se liší od původně kompilované funkce.</span><span class="sxs-lookup"><span data-stu-id="772da-115">The [ICorProfilerFunctionControl::SetILInstrumentedCodeMap](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) method is not implemented in the .NET Framework 4.5, so functions that have been JIT-recompiled cannot have an IL-to-native mapping that differs from the originally compiled function.</span></span> <span data-ttu-id="772da-116">V takovém případě nelze `GetILToNativeMapping2` volat pomocí nenulového rekompilovaného ID JIT v .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="772da-116">As such, `GetILToNativeMapping2` cannot be called with a nonzero JIT-recompiled ID in the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="772da-117">Metoda `GetILToNativeMapping2` vrací pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="772da-117">The `GetILToNativeMapping2` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="772da-118">Aby bylo možné určit, že některé rozsahy nativních instrukcí odpovídají zvláštním oblastem kódu (například Prolog), může být položka pole `ilOffset` nastavena na hodnotu výčtu [CorDebugIlToNativeMappingTypes –](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="772da-118">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="772da-119">Po `GetILToNativeMapping2` vrátí, je nutné ověřit, zda byla vyrovnávací paměť `map` dostatečně velká, aby obsahovala všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="772da-119">After `GetILToNativeMapping2` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="772da-120">To provedete tak, že porovnáte hodnotu `cMap` s hodnotou parametru `pcMap`.</span><span class="sxs-lookup"><span data-stu-id="772da-120">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="772da-121">Pokud je hodnota `pcMap`, když se vynásobí velikostí `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, je větší než `cMap`, přidělte větší `map` vyrovnávací paměť, aktualizujte `cMap` o novou, větší velikost a zavolejte `GetILToNativeMapping2` znovu.</span><span class="sxs-lookup"><span data-stu-id="772da-121">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping2` again.</span></span>  
  
 <span data-ttu-id="772da-122">Alternativně můžete pro získání správné velikosti vyrovnávací paměti nejprve volat `GetILToNativeMapping2` s nulovou délkou `map` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="772da-122">Alternatively, you can first call `GetILToNativeMapping2` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="772da-123">Pak můžete nastavit velikost vyrovnávací paměti na hodnotu vrácenou v `pcMap` a volat `GetILToNativeMapping2` znovu.</span><span class="sxs-lookup"><span data-stu-id="772da-123">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="772da-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="772da-124">Requirements</span></span>  
 <span data-ttu-id="772da-125">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="772da-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="772da-126">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="772da-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="772da-127">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="772da-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="772da-128">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="772da-128">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="772da-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="772da-129">See also</span></span>

- [<span data-ttu-id="772da-130">GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="772da-130">GetILToNativeMapping Method</span></span>](icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="772da-131">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="772da-131">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="772da-132">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="772da-132">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="772da-133">Profilace</span><span class="sxs-lookup"><span data-stu-id="772da-133">Profiling</span></span>](index.md)
