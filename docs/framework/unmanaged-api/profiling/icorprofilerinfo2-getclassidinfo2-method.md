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
ms.openlocfilehash: 64d2cd76dafb1a51814b916b5ce73fb08cdcaef9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868857"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a><span data-ttu-id="d56c1-102">ICorProfilerInfo2::GetClassIDInfo2 – metoda</span><span class="sxs-lookup"><span data-stu-id="d56c1-102">ICorProfilerInfo2::GetClassIDInfo2 Method</span></span>
<span data-ttu-id="d56c1-103">Získá nadřazený modul a token metadat pro otevřenou obecnou definici zadané třídy, `ClassID` své nadřazené třídy a `ClassID` pro každý argument typu, pokud je k dispozici pro třídu.</span><span class="sxs-lookup"><span data-stu-id="d56c1-103">Gets the parent module and metadata token for the open generic definition of the specified class, the `ClassID` of its parent class, and the `ClassID` for each type argument, if present, of the class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d56c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d56c1-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d56c1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d56c1-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="d56c1-106">pro ID třídy, pro kterou budou načteny informace.</span><span class="sxs-lookup"><span data-stu-id="d56c1-106">[in] The ID of the class for which information will be retrieved.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="d56c1-107">mimo Ukazatel na ID nadřazeného modulu pro otevřenou obecnou definici zadané třídy.</span><span class="sxs-lookup"><span data-stu-id="d56c1-107">[out] Pointer to the ID of the parent module for the open generic definition of the specified class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="d56c1-108">mimo Ukazatel na token metadat pro otevřenou obecnou definici zadané třídy.</span><span class="sxs-lookup"><span data-stu-id="d56c1-108">[out] Pointer to the metadata token for the open generic definition of the specified class.</span></span>  
  
 `pParentClassId`  
 <span data-ttu-id="d56c1-109">mimo Ukazatel na ID nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="d56c1-109">[out] Pointer to the ID of the parent class.</span></span>  
  
 `cNumTypeArgs`  
 <span data-ttu-id="d56c1-110">pro Velikost pole `typeArgs`.</span><span class="sxs-lookup"><span data-stu-id="d56c1-110">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcNumTypeArgs`  
 <span data-ttu-id="d56c1-111">mimo Ukazatel na celkový počet dostupných prvků.</span><span class="sxs-lookup"><span data-stu-id="d56c1-111">[out] Pointer to the total number of available elements.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="d56c1-112">mimo Pole hodnot `ClassID`, z nichž každá představuje ID argumentu typu třídy.</span><span class="sxs-lookup"><span data-stu-id="d56c1-112">[out] An array of `ClassID` values, each of which represents the ID of a type argument of the class.</span></span> <span data-ttu-id="d56c1-113">Když se metoda vrátí, `typeArgs` bude obsahovat některé nebo všechny dostupné `ClassID` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d56c1-113">When the method returns, `typeArgs` will contain some or all the available `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d56c1-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d56c1-114">Remarks</span></span>  
 <span data-ttu-id="d56c1-115">Metoda `GetClassIDInfo2` je podobná metodě [ICorProfilerInfo:: GetClassIDInfo –](icorprofilerinfo-getclassidinfo-method.md) , ale `GetClassIDInfo2` získá další informace o obecném typu.</span><span class="sxs-lookup"><span data-stu-id="d56c1-115">The `GetClassIDInfo2` method is similar to the [ICorProfilerInfo::GetClassIDInfo](icorprofilerinfo-getclassidinfo-method.md) method, but `GetClassIDInfo2` obtains additional information about a generic type.</span></span>  
  
 <span data-ttu-id="d56c1-116">Kód profileru může zavolat [ICorProfilerInfo:: GetModuleMetaData –](icorprofilerinfo-getmodulemetadata-method.md) a získat rozhraní [metadat](../../../../docs/framework/unmanaged-api/metadata/index.md) pro daný modul.</span><span class="sxs-lookup"><span data-stu-id="d56c1-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="d56c1-117">Token metadat, který je vrácen do umístění odkazovaného `pTypeDefToken` lze následně použít pro přístup k metadatům třídy.</span><span class="sxs-lookup"><span data-stu-id="d56c1-117">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="d56c1-118">Jakmile `GetClassIDInfo2` vrátí, je nutné ověřit, zda byla vyrovnávací paměť `typeArgs` dostatečně velká, aby obsahovala všechny `ClassID` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d56c1-118">After `GetClassIDInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="d56c1-119">To provedete tak, že porovnáte hodnotu, na kterou `pcNumTypeArgs` odkazuje, hodnotou `cNumTypeArgs` parametru.</span><span class="sxs-lookup"><span data-stu-id="d56c1-119">To do this, compare the value that `pcNumTypeArgs` points to with the value of the `cNumTypeArgs` parameter.</span></span> <span data-ttu-id="d56c1-120">Pokud `pcNumTypeArgs` odkazuje na hodnotu, která je větší než `cNumTypeArgs`, přidělte větší vyrovnávací paměť `typeArgs`, aktualizujte `cNumTypeArgs` novou, větší velikostí a zavolejte `GetClassIDInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="d56c1-120">If `pcNumTypeArgs` points to a value that is larger than `cNumTypeArgs`, allocate a larger `typeArgs` buffer, update `cNumTypeArgs` with the new, larger size, and call `GetClassIDInfo2` again.</span></span>  
  
 <span data-ttu-id="d56c1-121">Alternativně můžete pro získání správné velikosti vyrovnávací paměti nejprve volat `GetClassIDInfo2` s nulovou délkou `typeArgs` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d56c1-121">Alternatively, you can first call `GetClassIDInfo2` with a zero-length `typeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="d56c1-122">Pak můžete nastavit velikost vyrovnávací paměti `typeArgs` na hodnotu vrácenou v `pcNumTypeArgs` a volat `GetClassIDInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="d56c1-122">You can then set the `typeArgs` buffer size to the value returned in `pcNumTypeArgs` and call `GetClassIDInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d56c1-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d56c1-123">Requirements</span></span>  
 <span data-ttu-id="d56c1-124">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d56c1-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d56c1-125">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d56c1-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d56c1-126">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d56c1-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d56c1-127">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d56c1-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d56c1-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d56c1-128">See also</span></span>

- [<span data-ttu-id="d56c1-129">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d56c1-129">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="d56c1-130">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d56c1-130">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="d56c1-131">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d56c1-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="d56c1-132">Profilace</span><span class="sxs-lookup"><span data-stu-id="d56c1-132">Profiling</span></span>](index.md)
