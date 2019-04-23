---
title: ICorProfilerInfo2::GetClassLayout – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassLayout
helpviewer_keywords:
- ICorProfilerInfo2::GetClassLayout method [.NET Framework profiling]
- GetClassLayout method, ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: a3a36987-5666-4e2f-95b5-d0cb246502ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6dcb9d5b3f1f47d6613be90f181a98ce991f697a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134833"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a><span data-ttu-id="5818f-102">ICorProfilerInfo2::GetClassLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="5818f-102">ICorProfilerInfo2::GetClassLayout Method</span></span>
<span data-ttu-id="5818f-103">Získá informace o rozvržení, v paměti, pole definovaná pomocí dané třídy.</span><span class="sxs-lookup"><span data-stu-id="5818f-103">Gets information about the layout, in memory, of the fields defined by the specified class.</span></span> <span data-ttu-id="5818f-104">To znamená tato metoda načte posuny polí třídy.</span><span class="sxs-lookup"><span data-stu-id="5818f-104">That is, this method gets the offsets of the class's fields.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5818f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5818f-105">Syntax</span></span>  
  
```  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5818f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5818f-106">Parameters</span></span>  
 `classID`  
 <span data-ttu-id="5818f-107">[in] ID třídy, pro kterou budou načteny rozložení.</span><span class="sxs-lookup"><span data-stu-id="5818f-107">[in] The ID of the class for which the layout will be retrieved.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="5818f-108">[out v] Pole [cor_field_offset –](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) struktury, z nichž každý obsahuje tokeny a posuny polí třídy.</span><span class="sxs-lookup"><span data-stu-id="5818f-108">[in, out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which contains the tokens and offsets of the class's fields.</span></span>  
  
 `cFieldOffset`  
 <span data-ttu-id="5818f-109">[in] Velikost `rFieldOffset` pole.</span><span class="sxs-lookup"><span data-stu-id="5818f-109">[in] The size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="5818f-110">[out] Ukazatel na celkový počet elementů k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5818f-110">[out] A pointer to the total number of available elements.</span></span> <span data-ttu-id="5818f-111">Pokud `cFieldOffset` je 0, tato hodnota označuje počet prvků, které jsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="5818f-111">If `cFieldOffset` is 0, this value indicates the number of elements needed.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="5818f-112">[out] Ukazatel na umístění, které obsahuje velikost v bajtech třídy.</span><span class="sxs-lookup"><span data-stu-id="5818f-112">[out] A pointer to a location that contains the size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5818f-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5818f-113">Remarks</span></span>  
 <span data-ttu-id="5818f-114">`GetClassLayout` Metoda vrátí pouze pole definovaná pomocí vlastní třídy.</span><span class="sxs-lookup"><span data-stu-id="5818f-114">The `GetClassLayout` method returns only the fields defined by the class itself.</span></span> <span data-ttu-id="5818f-115">Pokud nadřazená třída třídy definoval také pole, musí volat profiler `GetClassLayout` na nadřazené třídu k získání těchto polí.</span><span class="sxs-lookup"><span data-stu-id="5818f-115">If the class's parent class has defined fields as well, the profiler must call `GetClassLayout` on the parent class to obtain those fields.</span></span>  
  
 <span data-ttu-id="5818f-116">Pokud používáte `GetClassLayout` s třídami řetězce, metoda selže s kódem chyby E_INVALIDARG.</span><span class="sxs-lookup"><span data-stu-id="5818f-116">If you use `GetClassLayout` with string classes, the method will fail with error code E_INVALIDARG.</span></span> <span data-ttu-id="5818f-117">Použití [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) a získat informace o rozložení řetězce.</span><span class="sxs-lookup"><span data-stu-id="5818f-117">Use [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) to get information about the layout of a string.</span></span> <span data-ttu-id="5818f-118">`GetClassLayout` také selže při volání s třídou pole.</span><span class="sxs-lookup"><span data-stu-id="5818f-118">`GetClassLayout` will also fail when called with an array class.</span></span>  
  
 <span data-ttu-id="5818f-119">Po `GetClassLayout` vrátí, musíte ověřit, že `rFieldOffset` vyrovnávací paměť je dostatečně velký, aby obsahovala všechny dostupné `COR_FIELD_OFFSET` struktury.</span><span class="sxs-lookup"><span data-stu-id="5818f-119">After `GetClassLayout` returns, you must verify that the `rFieldOffset` buffer was large enough to contain all the available `COR_FIELD_OFFSET` structures.</span></span> <span data-ttu-id="5818f-120">K tomuto účelu porovnat hodnoty, které `pcFieldOffset` odkazuje na s velikostí `rFieldOffset` rozdělené podle velikosti `COR_FIELD_OFFSET` struktury.</span><span class="sxs-lookup"><span data-stu-id="5818f-120">To do this, compare the value that `pcFieldOffset` points to with the size of `rFieldOffset` divided by the size of a `COR_FIELD_OFFSET` structure.</span></span> <span data-ttu-id="5818f-121">Pokud `rFieldOffset` není velký, přidělte větší `rFieldOffset` vyrovnávací paměti, aktualizujte `cFieldOffset` nové, větší velikosti a volání `GetClassLayout` znovu.</span><span class="sxs-lookup"><span data-stu-id="5818f-121">If `rFieldOffset` is not large enough, allocate a larger `rFieldOffset` buffer, update `cFieldOffset` with the new, larger size, and call `GetClassLayout` again.</span></span>  
  
 <span data-ttu-id="5818f-122">Alternativně můžete nejprve volat `GetClassLayout` s nulovou délkou `rFieldOffset` vyrovnávací paměť pro získání správné vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="5818f-122">Alternatively, you can first call `GetClassLayout` with a zero-length `rFieldOffset` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="5818f-123">Pak můžete nastavit velikost vyrovnávací paměti pro hodnotu vrácenou v `pcFieldOffset` a volat `GetClassLayout` znovu.</span><span class="sxs-lookup"><span data-stu-id="5818f-123">You can then set the buffer size to the value returned in `pcFieldOffset` and call `GetClassLayout` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5818f-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5818f-124">Requirements</span></span>  
 <span data-ttu-id="5818f-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5818f-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5818f-126">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5818f-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5818f-127">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5818f-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5818f-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5818f-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5818f-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5818f-129">See also</span></span>

- [<span data-ttu-id="5818f-130">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5818f-130">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="5818f-131">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5818f-131">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="5818f-132">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="5818f-132">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="5818f-133">Profilace</span><span class="sxs-lookup"><span data-stu-id="5818f-133">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
