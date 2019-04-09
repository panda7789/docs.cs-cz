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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b98746be189e211572e5517aac1f06825973b39
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168851"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a><span data-ttu-id="d1324-102">ICorProfilerInfo2::GetClassIDInfo2 – metoda</span><span class="sxs-lookup"><span data-stu-id="d1324-102">ICorProfilerInfo2::GetClassIDInfo2 Method</span></span>
<span data-ttu-id="d1324-103">Získá nadřazený modulu a metadata token pro definici otevřený obecný zadanou třídu, `ClassID` své nadřazené třídy a `ClassID` pro každý typ argumentu, pokud jsou k dispozici třídy.</span><span class="sxs-lookup"><span data-stu-id="d1324-103">Gets the parent module and metadata token for the open generic definition of the specified class, the `ClassID` of its parent class, and the `ClassID` for each type argument, if present, of the class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1324-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1324-104">Syntax</span></span>  
  
```  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1324-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1324-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="d1324-106">[in] ID třídy, pro kterou budou načteny informace.</span><span class="sxs-lookup"><span data-stu-id="d1324-106">[in] The ID of the class for which information will be retrieved.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="d1324-107">[out] Ukazatel na ID nadřazeného modulu pro definici otevřený obecný dané třídy.</span><span class="sxs-lookup"><span data-stu-id="d1324-107">[out] Pointer to the ID of the parent module for the open generic definition of the specified class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="d1324-108">[out] Ukazatel na token metadat pro definici otevřený obecný dané třídy.</span><span class="sxs-lookup"><span data-stu-id="d1324-108">[out] Pointer to the metadata token for the open generic definition of the specified class.</span></span>  
  
 `pParentClassId`  
 <span data-ttu-id="d1324-109">[out] Ukazatel na ID nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="d1324-109">[out] Pointer to the ID of the parent class.</span></span>  
  
 `cNumTypeArgs`  
 <span data-ttu-id="d1324-110">[in] Velikost `typeArgs` pole.</span><span class="sxs-lookup"><span data-stu-id="d1324-110">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcNumTypeArgs`  
 <span data-ttu-id="d1324-111">[out] Ukazatel na celkový počet elementů k dispozici.</span><span class="sxs-lookup"><span data-stu-id="d1324-111">[out] Pointer to the total number of available elements.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="d1324-112">[out] Pole `ClassID` hodnot, z nichž každý představuje ID argument typu třídy.</span><span class="sxs-lookup"><span data-stu-id="d1324-112">[out] An array of `ClassID` values, each of which represents the ID of a type argument of the class.</span></span> <span data-ttu-id="d1324-113">Po návratu metody `typeArgs` bude obsahovat některé nebo všechny dostupné `ClassID` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d1324-113">When the method returns, `typeArgs` will contain some or all the available `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1324-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d1324-114">Remarks</span></span>  
 <span data-ttu-id="d1324-115">`GetClassIDInfo2` Metoda je podobná [icorprofilerinfo::getclassidinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) metody, ale `GetClassIDInfo2` získá další informace o obecném typu.</span><span class="sxs-lookup"><span data-stu-id="d1324-115">The `GetClassIDInfo2` method is similar to the [ICorProfilerInfo::GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) method, but `GetClassIDInfo2` obtains additional information about a generic type.</span></span>  
  
 <span data-ttu-id="d1324-116">Profiler kódu může volat [icorprofilerinfo::getmodulemetadata –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) získat [metadat](../../../../docs/framework/unmanaged-api/metadata/index.md) rozhraní pro daný modul.</span><span class="sxs-lookup"><span data-stu-id="d1324-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="d1324-117">Token metadat, který je vrácen do umístění odkazuje `pTypeDefToken` lze použít k přístupu k metadatům pro třídu.</span><span class="sxs-lookup"><span data-stu-id="d1324-117">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="d1324-118">Po `GetClassIDInfo2` vrátí, musíte ověřit, že `typeArgs` vyrovnávací paměť je dostatečně velký, aby obsahovala všechny `ClassID` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d1324-118">After `GetClassIDInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="d1324-119">K tomuto účelu porovnat hodnoty, které `pcNumTypeArgs` odkazuje na hodnotu `cNumTypeArgs` parametru.</span><span class="sxs-lookup"><span data-stu-id="d1324-119">To do this, compare the value that `pcNumTypeArgs` points to with the value of the `cNumTypeArgs` parameter.</span></span> <span data-ttu-id="d1324-120">Pokud `pcNumTypeArgs` odkazuje na hodnotu, která je větší než `cNumTypeArgs`, přidělte větší `typeArgs` vyrovnávací paměti, aktualizujte `cNumTypeArgs` nové, větší velikosti a volání `GetClassIDInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="d1324-120">If `pcNumTypeArgs` points to a value that is larger than `cNumTypeArgs`, allocate a larger `typeArgs` buffer, update `cNumTypeArgs` with the new, larger size, and call `GetClassIDInfo2` again.</span></span>  
  
 <span data-ttu-id="d1324-121">Alternativně můžete nejprve volat `GetClassIDInfo2` s nulovou délkou `typeArgs` vyrovnávací paměť pro získání správné vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="d1324-121">Alternatively, you can first call `GetClassIDInfo2` with a zero-length `typeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="d1324-122">Pak můžete nastavit `typeArgs` velikost k hodnotě vrácené ve vyrovnávací paměti `pcNumTypeArgs` a volat `GetClassIDInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="d1324-122">You can then set the `typeArgs` buffer size to the value returned in `pcNumTypeArgs` and call `GetClassIDInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1324-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d1324-123">Requirements</span></span>  
 <span data-ttu-id="d1324-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1324-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1324-125">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d1324-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d1324-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1324-126">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d1324-127">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d1324-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d1324-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d1324-128">See also</span></span>

- [<span data-ttu-id="d1324-129">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1324-129">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="d1324-130">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1324-130">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="d1324-131">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d1324-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="d1324-132">Profilace</span><span class="sxs-lookup"><span data-stu-id="d1324-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
