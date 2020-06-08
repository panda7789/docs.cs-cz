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
ms.openlocfilehash: ac35b18ce8c45c95bb2fb8e820423470ca1b75bf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497150"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a><span data-ttu-id="060f8-102">ICorProfilerInfo2::GetClassLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="060f8-102">ICorProfilerInfo2::GetClassLayout Method</span></span>
<span data-ttu-id="060f8-103">Načte informace o rozložení v paměti polí definovaných specifikovanou třídou.</span><span class="sxs-lookup"><span data-stu-id="060f8-103">Gets information about the layout, in memory, of the fields defined by the specified class.</span></span> <span data-ttu-id="060f8-104">To znamená, že tato metoda získá posuny polí třídy.</span><span class="sxs-lookup"><span data-stu-id="060f8-104">That is, this method gets the offsets of the class's fields.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="060f8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="060f8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="060f8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="060f8-106">Parameters</span></span>  
 `classID`  
 <span data-ttu-id="060f8-107">pro ID třídy, pro kterou bude rozložení načteno.</span><span class="sxs-lookup"><span data-stu-id="060f8-107">[in] The ID of the class for which the layout will be retrieved.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="060f8-108">[in, out] Pole struktur [COR_FIELD_OFFSET](../metadata/cor-field-offset-structure.md) , z nichž každá obsahuje tokeny a posuny polí třídy.</span><span class="sxs-lookup"><span data-stu-id="060f8-108">[in, out] An array of [COR_FIELD_OFFSET](../metadata/cor-field-offset-structure.md) structures, each of which contains the tokens and offsets of the class's fields.</span></span>  
  
 `cFieldOffset`  
 <span data-ttu-id="060f8-109">pro Velikost `rFieldOffset` pole.</span><span class="sxs-lookup"><span data-stu-id="060f8-109">[in] The size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="060f8-110">mimo Ukazatel na celkový počet dostupných prvků.</span><span class="sxs-lookup"><span data-stu-id="060f8-110">[out] A pointer to the total number of available elements.</span></span> <span data-ttu-id="060f8-111">Pokud `cFieldOffset` je 0, tato hodnota označuje potřebný počet prvků.</span><span class="sxs-lookup"><span data-stu-id="060f8-111">If `cFieldOffset` is 0, this value indicates the number of elements needed.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="060f8-112">mimo Ukazatel na umístění, které obsahuje velikost (v bajtech) třídy.</span><span class="sxs-lookup"><span data-stu-id="060f8-112">[out] A pointer to a location that contains the size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="060f8-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="060f8-113">Remarks</span></span>  
 <span data-ttu-id="060f8-114">`GetClassLayout`Metoda vrátí pouze pole, která jsou definována samotný třídou.</span><span class="sxs-lookup"><span data-stu-id="060f8-114">The `GetClassLayout` method returns only the fields defined by the class itself.</span></span> <span data-ttu-id="060f8-115">Pokud má nadřazená třída třídy definována také pole, musí Profiler zavolat `GetClassLayout` na nadřazenou třídu, aby tato pole získala.</span><span class="sxs-lookup"><span data-stu-id="060f8-115">If the class's parent class has defined fields as well, the profiler must call `GetClassLayout` on the parent class to obtain those fields.</span></span>  
  
 <span data-ttu-id="060f8-116">Použijete `GetClassLayout` -li s řetězcovými třídami, metoda se nezdaří s kódem chyby E_INVALIDARG.</span><span class="sxs-lookup"><span data-stu-id="060f8-116">If you use `GetClassLayout` with string classes, the method will fail with error code E_INVALIDARG.</span></span> <span data-ttu-id="060f8-117">K získání informací o rozložení řetězce použijte [ICorProfilerInfo2:: GetStringLayout –](icorprofilerinfo2-getstringlayout-method.md) .</span><span class="sxs-lookup"><span data-stu-id="060f8-117">Use [ICorProfilerInfo2::GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) to get information about the layout of a string.</span></span> <span data-ttu-id="060f8-118">`GetClassLayout`selže také při volání s třídou Array.</span><span class="sxs-lookup"><span data-stu-id="060f8-118">`GetClassLayout` will also fail when called with an array class.</span></span>  
  
 <span data-ttu-id="060f8-119">Po `GetClassLayout` návratu je nutné ověřit, zda `rFieldOffset` byla vyrovnávací paměť dostatečně velká, aby obsahovala všechny dostupné `COR_FIELD_OFFSET` struktury.</span><span class="sxs-lookup"><span data-stu-id="060f8-119">After `GetClassLayout` returns, you must verify that the `rFieldOffset` buffer was large enough to contain all the available `COR_FIELD_OFFSET` structures.</span></span> <span data-ttu-id="060f8-120">Chcete-li to provést, porovnejte hodnotu, na kterou odkazuje, na `pcFieldOffset` Velikost `rFieldOffset` dělené velikostí `COR_FIELD_OFFSET` struktury.</span><span class="sxs-lookup"><span data-stu-id="060f8-120">To do this, compare the value that `pcFieldOffset` points to with the size of `rFieldOffset` divided by the size of a `COR_FIELD_OFFSET` structure.</span></span> <span data-ttu-id="060f8-121">Pokud `rFieldOffset` není dostatečně velká, přidělte větší `rFieldOffset` vyrovnávací paměť, aktualizujte `cFieldOffset` novou, větší velikost a zavolejte `GetClassLayout` znovu.</span><span class="sxs-lookup"><span data-stu-id="060f8-121">If `rFieldOffset` is not large enough, allocate a larger `rFieldOffset` buffer, update `cFieldOffset` with the new, larger size, and call `GetClassLayout` again.</span></span>  
  
 <span data-ttu-id="060f8-122">Případně můžete `GetClassLayout` pro získání správné velikosti vyrovnávací paměti nejprve zavolat s nulovou délkou `rFieldOffset` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="060f8-122">Alternatively, you can first call `GetClassLayout` with a zero-length `rFieldOffset` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="060f8-123">Pak můžete nastavit velikost vyrovnávací paměti na hodnotu vrácenou v `pcFieldOffset` a volat `GetClassLayout` znovu.</span><span class="sxs-lookup"><span data-stu-id="060f8-123">You can then set the buffer size to the value returned in `pcFieldOffset` and call `GetClassLayout` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="060f8-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="060f8-124">Requirements</span></span>  
 <span data-ttu-id="060f8-125">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="060f8-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="060f8-126">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="060f8-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="060f8-127">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="060f8-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="060f8-128">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="060f8-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="060f8-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="060f8-129">See also</span></span>

- [<span data-ttu-id="060f8-130">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="060f8-130">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="060f8-131">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="060f8-131">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="060f8-132">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="060f8-132">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="060f8-133">Profilace</span><span class="sxs-lookup"><span data-stu-id="060f8-133">Profiling</span></span>](index.md)
