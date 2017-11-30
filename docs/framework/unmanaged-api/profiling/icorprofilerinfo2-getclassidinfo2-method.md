---
title: "ICorProfilerInfo2::GetClassIDInfo2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetClassIDInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetClassIDInfo2
helpviewer_keywords:
- GetClassIDInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassIDInfo2 method [.NET Framework profiling]
ms.assetid: 0141d582-d066-4d49-8d1f-ae82129a1960
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8bfa970acd21a518112dd6ee9228b621758e49f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a><span data-ttu-id="d2846-102">ICorProfilerInfo2::GetClassIDInfo2 – metoda</span><span class="sxs-lookup"><span data-stu-id="d2846-102">ICorProfilerInfo2::GetClassIDInfo2 Method</span></span>
<span data-ttu-id="d2846-103">Získá nadřazený modulu a metadata token pro definici otevřený obecný pro zadanou třídu, `ClassID` ze své nadřízené třídy a `ClassID` pro každý typ argumentu, pokud existuje, třídy.</span><span class="sxs-lookup"><span data-stu-id="d2846-103">Gets the parent module and metadata token for the open generic definition of the specified class, the `ClassID` of its parent class, and the `ClassID` for each type argument, if present, of the class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2846-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2846-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="d2846-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2846-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="d2846-106">[v] ID třídy, pro které budou načteny informace.</span><span class="sxs-lookup"><span data-stu-id="d2846-106">[in] The ID of the class for which information will be retrieved.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="d2846-107">[out] Ukazatel na ID nadřazeného modulu pro definici otevřený obecný pro zadanou třídu.</span><span class="sxs-lookup"><span data-stu-id="d2846-107">[out] Pointer to the ID of the parent module for the open generic definition of the specified class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="d2846-108">[out] Ukazatel na token metadata pro definici otevřený obecný pro zadanou třídu.</span><span class="sxs-lookup"><span data-stu-id="d2846-108">[out] Pointer to the metadata token for the open generic definition of the specified class.</span></span>  
  
 `pParentClassId`  
 <span data-ttu-id="d2846-109">[out] Ukazatel na ID nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="d2846-109">[out] Pointer to the ID of the parent class.</span></span>  
  
 `cNumTypeArgs`  
 <span data-ttu-id="d2846-110">[v] Velikost `typeArgs` pole.</span><span class="sxs-lookup"><span data-stu-id="d2846-110">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcNumTypeArgs`  
 <span data-ttu-id="d2846-111">[out] Ukazatel na celkový počet elementů k dispozici.</span><span class="sxs-lookup"><span data-stu-id="d2846-111">[out] Pointer to the total number of available elements.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="d2846-112">[out] Pole `ClassID` hodnoty, z nichž každý představuje ID argument typu třídy.</span><span class="sxs-lookup"><span data-stu-id="d2846-112">[out] An array of `ClassID` values, each of which represents the ID of a type argument of the class.</span></span> <span data-ttu-id="d2846-113">Po návratu metody `typeArgs` bude obsahovat některé nebo všechny dostupných `ClassID` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d2846-113">When the method returns, `typeArgs` will contain some or all the available `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2846-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d2846-114">Remarks</span></span>  
 <span data-ttu-id="d2846-115">`GetClassIDInfo2` Metoda je podobná [icorprofilerinfo::getclassidinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) metoda, ale `GetClassIDInfo2` získá další informace o obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d2846-115">The `GetClassIDInfo2` method is similar to the [ICorProfilerInfo::GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) method, but `GetClassIDInfo2` obtains additional information about a generic type.</span></span>  
  
 <span data-ttu-id="d2846-116">Můžete volat kód profileru [icorprofilerinfo::getmodulemetadata –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) získat [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) rozhraní pro daného modulu.</span><span class="sxs-lookup"><span data-stu-id="d2846-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="d2846-117">Metadata token, který je vrácen do umístění odkazuje `pTypeDefToken` pak lze získat přístup k metadatům pro třídu.</span><span class="sxs-lookup"><span data-stu-id="d2846-117">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="d2846-118">Po `GetClassIDInfo2` vrátí, musíte ověřit, že `typeArgs` vyrovnávací paměť byla dostatečně velký pro obsahovat všechny `ClassID` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d2846-118">After `GetClassIDInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="d2846-119">K tomuto účelu porovnat hodnotu, `pcNumTypeArgs` body s hodnotou `cNumTypeArgs` parametr.</span><span class="sxs-lookup"><span data-stu-id="d2846-119">To do this, compare the value that `pcNumTypeArgs` points to with the value of the `cNumTypeArgs` parameter.</span></span> <span data-ttu-id="d2846-120">Pokud `pcNumTypeArgs` odkazuje na hodnotu, která je větší než `cNumTypeArgs`, přidělit větší `typeArgs` vyrovnávací paměti, aktualizujte `cNumTypeArgs` s novou, větší velikost a volání `GetClassIDInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="d2846-120">If `pcNumTypeArgs` points to a value that is larger than `cNumTypeArgs`, allocate a larger `typeArgs` buffer, update `cNumTypeArgs` with the new, larger size, and call `GetClassIDInfo2` again.</span></span>  
  
 <span data-ttu-id="d2846-121">Alternativně můžete nejdřív volat `GetClassIDInfo2` s nulovou délkou `typeArgs` vyrovnávací paměti se získat velikost správné vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d2846-121">Alternatively, you can first call `GetClassIDInfo2` with a zero-length `typeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="d2846-122">Pak můžete nastavit `typeArgs` velikost k hodnotě vrácené ve vyrovnávací paměti `pcNumTypeArgs` a volání `GetClassIDInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="d2846-122">You can then set the `typeArgs` buffer size to the value returned in `pcNumTypeArgs` and call `GetClassIDInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2846-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d2846-123">Requirements</span></span>  
 <span data-ttu-id="d2846-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2846-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2846-125">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d2846-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d2846-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2846-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2846-127">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2846-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2846-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2846-128">See Also</span></span>  
 [<span data-ttu-id="d2846-129">Icorprofilerinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2846-129">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="d2846-130">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2846-130">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="d2846-131">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d2846-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="d2846-132">Profilace</span><span class="sxs-lookup"><span data-stu-id="d2846-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
