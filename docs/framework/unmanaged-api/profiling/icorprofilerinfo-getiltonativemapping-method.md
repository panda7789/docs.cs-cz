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
ms.openlocfilehash: b3c0bee44bf49c7966b8fefcfe6460c6255375c5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502987"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a><span data-ttu-id="b9305-102">ICorProfilerInfo::GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="b9305-102">ICorProfilerInfo::GetILToNativeMapping Method</span></span>
<span data-ttu-id="b9305-103">Získá mapu z posunu od jazyka MSIL (Microsoft Intermediate Language) k nativním posunům pro kód obsažený v zadané funkci.</span><span class="sxs-lookup"><span data-stu-id="b9305-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9305-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9305-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9305-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b9305-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b9305-106">pro ID funkce, která obsahuje kód.</span><span class="sxs-lookup"><span data-stu-id="b9305-106">[in] The ID of the function that contains the code.</span></span>  
  
 `cMap`  
 <span data-ttu-id="b9305-107">pro Maximální velikost `map` pole.</span><span class="sxs-lookup"><span data-stu-id="b9305-107">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="b9305-108">mimo Celkový počet dostupných COR_DEBUG_IL_TO_NATIVE_MAP struktur.</span><span class="sxs-lookup"><span data-stu-id="b9305-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="b9305-109">mimo Pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktur, z nichž každý Určuje posun.</span><span class="sxs-lookup"><span data-stu-id="b9305-109">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="b9305-110">Poté `GetILToNativeMapping` , co metoda vrátí, `map` bude obsahovat některé nebo všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="b9305-110">After the `GetILToNativeMapping` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9305-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b9305-111">Remarks</span></span>  
 <span data-ttu-id="b9305-112">`GetILToNativeMapping`Metoda vrací pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktur.</span><span class="sxs-lookup"><span data-stu-id="b9305-112">The `GetILToNativeMapping` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="b9305-113">Aby bylo možné určit, že některé rozsahy nativních instrukcí odpovídají zvláštním oblastem kódu (například Prolog), položka v poli může mít své `ilOffset` pole nastaveno na hodnotu výčtu [CorDebugIlToNativeMappingTypes –](../debugging/cordebugiltonativemappingtypes-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="b9305-113">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="b9305-114">Po `GetILToNativeMapping` návratu je nutné ověřit, zda `map` byla vyrovnávací paměť dostatečně velká, aby obsahovala všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="b9305-114">After `GetILToNativeMapping` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="b9305-115">Chcete-li to provést, porovnejte hodnotu `cMap` s hodnotou `pcMap` parametru.</span><span class="sxs-lookup"><span data-stu-id="b9305-115">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="b9305-116">Pokud je `pcMap` hodnota, když je vynásobena velikostí `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, větší než `cMap` , přidělte větší `map` vyrovnávací paměť, aktualizujte `cMap` novou, větší velikost a zavolejte `GetILToNativeMapping` znovu.</span><span class="sxs-lookup"><span data-stu-id="b9305-116">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping` again.</span></span>  
  
 <span data-ttu-id="b9305-117">Případně můžete `GetILToNativeMapping` pro získání správné velikosti vyrovnávací paměti nejprve zavolat s nulovou délkou `map` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="b9305-117">Alternatively, you can first call `GetILToNativeMapping` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="b9305-118">Pak můžete nastavit velikost vyrovnávací paměti na hodnotu vrácenou v `pcMap` a volat `GetILToNativeMapping` znovu.</span><span class="sxs-lookup"><span data-stu-id="b9305-118">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9305-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b9305-119">Requirements</span></span>  
 <span data-ttu-id="b9305-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9305-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9305-121">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b9305-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b9305-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b9305-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9305-123">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9305-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9305-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9305-124">See also</span></span>

- [<span data-ttu-id="b9305-125">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9305-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="b9305-126">GetILToNativeMapping2 – metoda</span><span class="sxs-lookup"><span data-stu-id="b9305-126">GetILToNativeMapping2 Method</span></span>](icorprofilerinfo4-getiltonativemapping2-method.md)
- [<span data-ttu-id="b9305-127">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="b9305-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="b9305-128">Profilace</span><span class="sxs-lookup"><span data-stu-id="b9305-128">Profiling</span></span>](index.md)
