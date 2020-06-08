---
title: ICorProfilerInfo2::GetClassIDInfo2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassIDInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassIDInfo2
helpviewer_keywords:
- GetClassIDInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassIDInfo2 method [.NET Framework profiling]
ms.assetid: 0141d582-d066-4d49-8d1f-ae82129a1960
topic_type:
- apiref
ms.openlocfilehash: a33e51969dc0579d976f08470ebc6e2bcca04dd7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497163"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a><span data-ttu-id="4f640-102">ICorProfilerInfo2::GetClassIDInfo2 – metoda</span><span class="sxs-lookup"><span data-stu-id="4f640-102">ICorProfilerInfo2::GetClassIDInfo2 Method</span></span>
<span data-ttu-id="4f640-103">Získá nadřazený modul a token metadat pro otevřenou obecnou definici zadané třídy, `ClassID` její nadřazené třídy a `ClassID` pro každý argument typu (Pokud je k dispozici) třídy.</span><span class="sxs-lookup"><span data-stu-id="4f640-103">Gets the parent module and metadata token for the open generic definition of the specified class, the `ClassID` of its parent class, and the `ClassID` for each type argument, if present, of the class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f640-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f640-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f640-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f640-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="4f640-106">pro ID třídy, pro kterou budou načteny informace.</span><span class="sxs-lookup"><span data-stu-id="4f640-106">[in] The ID of the class for which information will be retrieved.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="4f640-107">mimo Ukazatel na ID nadřazeného modulu pro otevřenou obecnou definici zadané třídy.</span><span class="sxs-lookup"><span data-stu-id="4f640-107">[out] Pointer to the ID of the parent module for the open generic definition of the specified class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="4f640-108">mimo Ukazatel na token metadat pro otevřenou obecnou definici zadané třídy.</span><span class="sxs-lookup"><span data-stu-id="4f640-108">[out] Pointer to the metadata token for the open generic definition of the specified class.</span></span>  
  
 `pParentClassId`  
 <span data-ttu-id="4f640-109">mimo Ukazatel na ID nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="4f640-109">[out] Pointer to the ID of the parent class.</span></span>  
  
 `cNumTypeArgs`  
 <span data-ttu-id="4f640-110">pro Velikost `typeArgs` pole.</span><span class="sxs-lookup"><span data-stu-id="4f640-110">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcNumTypeArgs`  
 <span data-ttu-id="4f640-111">mimo Ukazatel na celkový počet dostupných prvků.</span><span class="sxs-lookup"><span data-stu-id="4f640-111">[out] Pointer to the total number of available elements.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="4f640-112">mimo Pole `ClassID` hodnot, z nichž každá představuje ID argumentu typu třídy.</span><span class="sxs-lookup"><span data-stu-id="4f640-112">[out] An array of `ClassID` values, each of which represents the ID of a type argument of the class.</span></span> <span data-ttu-id="4f640-113">Když se metoda vrátí, `typeArgs` bude obsahovat některé nebo všechny dostupné `ClassID` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4f640-113">When the method returns, `typeArgs` will contain some or all the available `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f640-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4f640-114">Remarks</span></span>  
 <span data-ttu-id="4f640-115">`GetClassIDInfo2`Metoda je podobná metodě [ICorProfilerInfo:: GetClassIDInfo –](icorprofilerinfo-getclassidinfo-method.md) , ale `GetClassIDInfo2` získá další informace o obecném typu.</span><span class="sxs-lookup"><span data-stu-id="4f640-115">The `GetClassIDInfo2` method is similar to the [ICorProfilerInfo::GetClassIDInfo](icorprofilerinfo-getclassidinfo-method.md) method, but `GetClassIDInfo2` obtains additional information about a generic type.</span></span>  
  
 <span data-ttu-id="4f640-116">Kód profileru může zavolat [ICorProfilerInfo:: GetModuleMetaData –](icorprofilerinfo-getmodulemetadata-method.md) a získat rozhraní [metadat](../metadata/index.md) pro daný modul.</span><span class="sxs-lookup"><span data-stu-id="4f640-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="4f640-117">Token metadat, který je vrácen do umístění odkazovaného pomocí, `pTypeDefToken` lze následně použít pro přístup k metadatům třídy.</span><span class="sxs-lookup"><span data-stu-id="4f640-117">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="4f640-118">Po `GetClassIDInfo2` návratu je nutné ověřit, zda `typeArgs` byla vyrovnávací paměť dostatečně velká, aby obsahovala všechny `ClassID` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4f640-118">After `GetClassIDInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="4f640-119">Provedete to tak, že porovnáte hodnotu, `pcNumTypeArgs` na kterou odkazuje, s hodnotou `cNumTypeArgs` parametru.</span><span class="sxs-lookup"><span data-stu-id="4f640-119">To do this, compare the value that `pcNumTypeArgs` points to with the value of the `cNumTypeArgs` parameter.</span></span> <span data-ttu-id="4f640-120">Pokud `pcNumTypeArgs` odkazuje na hodnotu, která je větší než `cNumTypeArgs` , přidělte větší `typeArgs` vyrovnávací paměť, aktualizujte `cNumTypeArgs` novou, větší velikost a zavolejte `GetClassIDInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="4f640-120">If `pcNumTypeArgs` points to a value that is larger than `cNumTypeArgs`, allocate a larger `typeArgs` buffer, update `cNumTypeArgs` with the new, larger size, and call `GetClassIDInfo2` again.</span></span>  
  
 <span data-ttu-id="4f640-121">Případně můžete `GetClassIDInfo2` pro získání správné velikosti vyrovnávací paměti nejprve zavolat s nulovou délkou `typeArgs` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4f640-121">Alternatively, you can first call `GetClassIDInfo2` with a zero-length `typeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="4f640-122">Pak můžete nastavit `typeArgs` Velikost vyrovnávací paměti na hodnotu vrácenou v `pcNumTypeArgs` a volat `GetClassIDInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="4f640-122">You can then set the `typeArgs` buffer size to the value returned in `pcNumTypeArgs` and call `GetClassIDInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f640-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4f640-123">Requirements</span></span>  
 <span data-ttu-id="4f640-124">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f640-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f640-125">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4f640-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4f640-126">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4f640-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f640-127">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f640-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f640-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f640-128">See also</span></span>

- [<span data-ttu-id="4f640-129">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4f640-129">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="4f640-130">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4f640-130">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="4f640-131">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="4f640-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="4f640-132">Profilace</span><span class="sxs-lookup"><span data-stu-id="4f640-132">Profiling</span></span>](index.md)
