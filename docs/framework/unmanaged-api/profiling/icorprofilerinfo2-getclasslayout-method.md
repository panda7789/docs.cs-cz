---
title: "ICorProfilerInfo2::GetClassLayout – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetClassLayout
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetClassLayout
helpviewer_keywords:
- ICorProfilerInfo2::GetClassLayout method [.NET Framework profiling]
- GetClassLayout method, ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: a3a36987-5666-4e2f-95b5-d0cb246502ec
topic_type: apiref
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9dcee307dd7e852719a1309d9c29202567cde2e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getclasslayout-method"></a><span data-ttu-id="96b3c-102">ICorProfilerInfo2::GetClassLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="96b3c-102">ICorProfilerInfo2::GetClassLayout Method</span></span>
<span data-ttu-id="96b3c-103">Získá informace o rozložení, v paměti pro pole definovaná v zadané třídě.</span><span class="sxs-lookup"><span data-stu-id="96b3c-103">Gets information about the layout, in memory, of the fields defined by the specified class.</span></span> <span data-ttu-id="96b3c-104">To znamená tato metoda získá posun třída polí.</span><span class="sxs-lookup"><span data-stu-id="96b3c-104">That is, this method gets the offsets of the class's fields.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96b3c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96b3c-105">Syntax</span></span>  
  
```  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="96b3c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="96b3c-106">Parameters</span></span>  
 `classID`  
 <span data-ttu-id="96b3c-107">[v] ID třídy, pro kterou bude načten rozložení.</span><span class="sxs-lookup"><span data-stu-id="96b3c-107">[in] The ID of the class for which the layout will be retrieved.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="96b3c-108">[ve out] Pole [cor_field_offset –](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) struktury, z nichž každý obsahuje tokenů a posuny polí třídu.</span><span class="sxs-lookup"><span data-stu-id="96b3c-108">[in, out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which contains the tokens and offsets of the class's fields.</span></span>  
  
 `cFieldOffset`  
 <span data-ttu-id="96b3c-109">[v] Velikost `rFieldOffset` pole.</span><span class="sxs-lookup"><span data-stu-id="96b3c-109">[in] The size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="96b3c-110">[out] Ukazatel na celkový počet elementů k dispozici.</span><span class="sxs-lookup"><span data-stu-id="96b3c-110">[out] A pointer to the total number of available elements.</span></span> <span data-ttu-id="96b3c-111">Pokud `cFieldOffset` je 0, tato hodnota označuje počet elementů potřeby.</span><span class="sxs-lookup"><span data-stu-id="96b3c-111">If `cFieldOffset` is 0, this value indicates the number of elements needed.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="96b3c-112">[out] Ukazatel na umístění, které obsahuje velikost v bajtech třídy.</span><span class="sxs-lookup"><span data-stu-id="96b3c-112">[out] A pointer to a location that contains the size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96b3c-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96b3c-113">Remarks</span></span>  
 <span data-ttu-id="96b3c-114">`GetClassLayout` Metoda vrátí pouze pole definované vlastní třídy.</span><span class="sxs-lookup"><span data-stu-id="96b3c-114">The `GetClassLayout` method returns only the fields defined by the class itself.</span></span> <span data-ttu-id="96b3c-115">Pokud třída nadřazené třídy, který definuje také pole, musí volat profileru `GetClassLayout` na nadřazené třídy k získání těchto polí.</span><span class="sxs-lookup"><span data-stu-id="96b3c-115">If the class's parent class has defined fields as well, the profiler must call `GetClassLayout` on the parent class to obtain those fields.</span></span>  
  
 <span data-ttu-id="96b3c-116">Pokud používáte `GetClassLayout` s třídami řetězce, metoda selže s kódem chyby E_INVALIDARG.</span><span class="sxs-lookup"><span data-stu-id="96b3c-116">If you use `GetClassLayout` with string classes, the method will fail with error code E_INVALIDARG.</span></span> <span data-ttu-id="96b3c-117">Použití [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) se získat informace o rozložení řetězce.</span><span class="sxs-lookup"><span data-stu-id="96b3c-117">Use [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) to get information about the layout of a string.</span></span> <span data-ttu-id="96b3c-118">`GetClassLayout`selžou i při volání s třídu pole.</span><span class="sxs-lookup"><span data-stu-id="96b3c-118">`GetClassLayout` will also fail when called with an array class.</span></span>  
  
 <span data-ttu-id="96b3c-119">Po `GetClassLayout` vrátí, musíte ověřit, že `rFieldOffset` vyrovnávací paměť byla dostatečně velký, aby se tak, aby obsahovala všechny dostupné `COR_FIELD_OFFSET` struktury.</span><span class="sxs-lookup"><span data-stu-id="96b3c-119">After `GetClassLayout` returns, you must verify that the `rFieldOffset` buffer was large enough to contain all the available `COR_FIELD_OFFSET` structures.</span></span> <span data-ttu-id="96b3c-120">K tomuto účelu porovnat hodnotu, `pcFieldOffset` body s velikostí `rFieldOffset` dělený velikost `COR_FIELD_OFFSET` struktury.</span><span class="sxs-lookup"><span data-stu-id="96b3c-120">To do this, compare the value that `pcFieldOffset` points to with the size of `rFieldOffset` divided by the size of a `COR_FIELD_OFFSET` structure.</span></span> <span data-ttu-id="96b3c-121">Pokud `rFieldOffset` není velký, přidělit větší `rFieldOffset` vyrovnávací paměti, aktualizujte `cFieldOffset` s novou, větší velikost a volání `GetClassLayout` znovu.</span><span class="sxs-lookup"><span data-stu-id="96b3c-121">If `rFieldOffset` is not large enough, allocate a larger `rFieldOffset` buffer, update `cFieldOffset` with the new, larger size, and call `GetClassLayout` again.</span></span>  
  
 <span data-ttu-id="96b3c-122">Alternativně můžete nejdřív volat `GetClassLayout` s nulovou délkou `rFieldOffset` vyrovnávací paměti se získat velikost správné vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="96b3c-122">Alternatively, you can first call `GetClassLayout` with a zero-length `rFieldOffset` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="96b3c-123">Velikost vyrovnávací paměti pak můžete nastavit na hodnotu, vrátí se v `pcFieldOffset` a volání `GetClassLayout` znovu.</span><span class="sxs-lookup"><span data-stu-id="96b3c-123">You can then set the buffer size to the value returned in `pcFieldOffset` and call `GetClassLayout` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96b3c-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="96b3c-124">Requirements</span></span>  
 <span data-ttu-id="96b3c-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96b3c-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96b3c-126">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="96b3c-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="96b3c-127">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96b3c-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96b3c-128">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96b3c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96b3c-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="96b3c-129">See Also</span></span>  
 [<span data-ttu-id="96b3c-130">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96b3c-130">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="96b3c-131">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96b3c-131">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="96b3c-132">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="96b3c-132">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="96b3c-133">Profilace</span><span class="sxs-lookup"><span data-stu-id="96b3c-133">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
