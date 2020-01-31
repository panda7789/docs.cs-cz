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
ms.openlocfilehash: f9abb3ae9cd3f9c70485e584399a6ed32b32a572
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76870613"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a><span data-ttu-id="5011e-102">ICorProfilerInfo::GetILToNativeMapping – metoda</span><span class="sxs-lookup"><span data-stu-id="5011e-102">ICorProfilerInfo::GetILToNativeMapping Method</span></span>
<span data-ttu-id="5011e-103">Získá mapu z posunu od jazyka MSIL (Microsoft Intermediate Language) k nativním posunům pro kód obsažený v zadané funkci.</span><span class="sxs-lookup"><span data-stu-id="5011e-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5011e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5011e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5011e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5011e-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="5011e-106">pro ID funkce, která obsahuje kód.</span><span class="sxs-lookup"><span data-stu-id="5011e-106">[in] The ID of the function that contains the code.</span></span>  
  
 `cMap`  
 <span data-ttu-id="5011e-107">pro Maximální velikost `map` pole</span><span class="sxs-lookup"><span data-stu-id="5011e-107">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="5011e-108">mimo Celkový počet dostupných COR_DEBUG_IL_TO_NATIVE_MAP struktur.</span><span class="sxs-lookup"><span data-stu-id="5011e-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="5011e-109">mimo Pole struktur `COR_DEBUG_IL_TO_NATIVE_MAP`, z nichž každý Určuje posun.</span><span class="sxs-lookup"><span data-stu-id="5011e-109">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="5011e-110">Po návratu metody `GetILToNativeMapping` bude `map` obsahovat některé nebo všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="5011e-110">After the `GetILToNativeMapping` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5011e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5011e-111">Remarks</span></span>  
 <span data-ttu-id="5011e-112">Metoda `GetILToNativeMapping` vrací pole `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="5011e-112">The `GetILToNativeMapping` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="5011e-113">Aby bylo možné určit, že některé rozsahy nativních instrukcí odpovídají zvláštním oblastem kódu (například Prolog), může být položka pole `ilOffset` nastavena na hodnotu výčtu [CorDebugIlToNativeMappingTypes –](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="5011e-113">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="5011e-114">Po `GetILToNativeMapping` vrátí, je nutné ověřit, zda byla vyrovnávací paměť `map` dostatečně velká, aby obsahovala všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="5011e-114">After `GetILToNativeMapping` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="5011e-115">To provedete tak, že porovnáte hodnotu `cMap` s hodnotou parametru `pcMap`.</span><span class="sxs-lookup"><span data-stu-id="5011e-115">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="5011e-116">Pokud je hodnota `pcMap`, když se vynásobí velikostí `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, je větší než `cMap`, přidělte větší `map` vyrovnávací paměť, aktualizujte `cMap` o novou, větší velikost a zavolejte `GetILToNativeMapping` znovu.</span><span class="sxs-lookup"><span data-stu-id="5011e-116">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping` again.</span></span>  
  
 <span data-ttu-id="5011e-117">Alternativně můžete pro získání správné velikosti vyrovnávací paměti nejprve volat `GetILToNativeMapping` s nulovou délkou `map` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="5011e-117">Alternatively, you can first call `GetILToNativeMapping` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="5011e-118">Pak můžete nastavit velikost vyrovnávací paměti na hodnotu vrácenou v `pcMap` a volat `GetILToNativeMapping` znovu.</span><span class="sxs-lookup"><span data-stu-id="5011e-118">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5011e-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5011e-119">Requirements</span></span>  
 <span data-ttu-id="5011e-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5011e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5011e-121">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5011e-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5011e-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5011e-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5011e-123">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5011e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5011e-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5011e-124">See also</span></span>

- [<span data-ttu-id="5011e-125">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5011e-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="5011e-126">GetILToNativeMapping2 – metoda</span><span class="sxs-lookup"><span data-stu-id="5011e-126">GetILToNativeMapping2 Method</span></span>](icorprofilerinfo4-getiltonativemapping2-method.md)
- [<span data-ttu-id="5011e-127">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="5011e-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="5011e-128">Profilace</span><span class="sxs-lookup"><span data-stu-id="5011e-128">Profiling</span></span>](index.md)
