---
title: ICorProfilerInfo2::GetFunctionInfo2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionInfo2
helpviewer_keywords:
- GetFunctionInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetFunctionInfo2 method [.NET Framework profiling]
ms.assetid: 0aa60f24-8bbd-4c83-83c5-86ad191b1d82
topic_type:
- apiref
ms.openlocfilehash: 11f9a186f5ec5e3b9e718a3ccd43b35b66d28078
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433187"
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a><span data-ttu-id="6ad99-102">ICorProfilerInfo2::GetFunctionInfo2 – metoda</span><span class="sxs-lookup"><span data-stu-id="6ad99-102">ICorProfilerInfo2::GetFunctionInfo2 Method</span></span>
<span data-ttu-id="6ad99-103">Získá nadřazenou třídu, token metadat a `ClassID` každého argumentu typu, pokud je k dispozici funkce.</span><span class="sxs-lookup"><span data-stu-id="6ad99-103">Gets the parent class, the metadata token, and the `ClassID` of each type argument, if present, of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ad99-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ad99-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionInfo2(  
    [in]  FunctionID funcId,  
    [in]  COR_PRF_FRAME_INFO frameInfo,  
    [out] ClassID *pClassId,  
    [out] ModuleID *pModuleId,  
    [out] mdToken *pToken,  
    [in]  ULONG32 cTypeArgs,  
    [out] ULONG32 *pcTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ad99-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ad99-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="6ad99-106">pro ID funkce, pro kterou se má získat nadřazená třída a další informace</span><span class="sxs-lookup"><span data-stu-id="6ad99-106">[in] The ID of the function for which to get the parent class and other information.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="6ad99-107">pro Hodnota `COR_PRF_FRAME_INFO`, která odkazuje na informace o snímku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="6ad99-107">[in] A `COR_PRF_FRAME_INFO` value that points to information about a stack frame.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="6ad99-108">mimo Ukazatel na nadřazenou třídu funkce.</span><span class="sxs-lookup"><span data-stu-id="6ad99-108">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="6ad99-109">mimo Ukazatel na modul, ve kterém je definována nadřazená třída funkce.</span><span class="sxs-lookup"><span data-stu-id="6ad99-109">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="6ad99-110">mimo Ukazatel na token metadat pro funkci.</span><span class="sxs-lookup"><span data-stu-id="6ad99-110">[out] A pointer to the metadata token for the function.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="6ad99-111">pro Velikost pole `typeArgs`.</span><span class="sxs-lookup"><span data-stu-id="6ad99-111">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcTypeArgs`  
 <span data-ttu-id="6ad99-112">mimo Ukazatel na celkový počet `ClassID`ch hodnot.</span><span class="sxs-lookup"><span data-stu-id="6ad99-112">[out] A pointer to the total number of `ClassID` values.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="6ad99-113">mimo Pole hodnot `ClassID`, z nichž každý je ID argumentu funkce.</span><span class="sxs-lookup"><span data-stu-id="6ad99-113">[out] An array of `ClassID` values, each of which is the ID of a type argument of the function.</span></span> <span data-ttu-id="6ad99-114">Když se metoda vrátí, `typeArgs` bude obsahovat některé nebo všechny `ClassID` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6ad99-114">When the method returns, `typeArgs` will contain some or all of the `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ad99-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ad99-115">Remarks</span></span>  
 <span data-ttu-id="6ad99-116">Kód profileru může zavolat [ICorProfilerInfo:: GetModuleMetaData –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) a získat rozhraní [metadat](../../../../docs/framework/unmanaged-api/metadata/index.md) pro daný modul.</span><span class="sxs-lookup"><span data-stu-id="6ad99-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="6ad99-117">Token metadat, který je vrácen do umístění odkazovaného `pToken` lze následně použít pro přístup k metadatům funkce.</span><span class="sxs-lookup"><span data-stu-id="6ad99-117">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="6ad99-118">IDENTIFIKÁTOR třídy a argumenty typu, které jsou vráceny pomocí `pClassId` a parametry `typeArgs` závisí na hodnotě předané v parametru `frameInfo`, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="6ad99-118">The class ID and type arguments that are returned through the `pClassId` and `typeArgs` parameters depend on the value that is passed in the `frameInfo` parameter, as shown in the following table.</span></span>  
  
|<span data-ttu-id="6ad99-119">Hodnota parametru `frameInfo`</span><span class="sxs-lookup"><span data-stu-id="6ad99-119">Value of the `frameInfo` parameter</span></span>|<span data-ttu-id="6ad99-120">Výsledek</span><span class="sxs-lookup"><span data-stu-id="6ad99-120">Result</span></span>|  
|----------------------------------------|------------|  
|<span data-ttu-id="6ad99-121">Hodnota `COR_PRF_FRAME_INFO` získaná z zpětného volání `FunctionEnter2`</span><span class="sxs-lookup"><span data-stu-id="6ad99-121">A `COR_PRF_FRAME_INFO` value that was obtained from a `FunctionEnter2` callback</span></span>|<span data-ttu-id="6ad99-122">`ClassID`vrácená v umístění, na které odkazuje `pClassId`a všechny argumenty typu vrácené v poli `typeArgs`, budou přesně.</span><span class="sxs-lookup"><span data-stu-id="6ad99-122">The `ClassID`, returned in the location referenced by `pClassId`, and all type arguments, returned in the `typeArgs` array, will be exact.</span></span>|  
|<span data-ttu-id="6ad99-123">`COR_PRF_FRAME_INFO` získaný ze zdroje jiného než zpětné volání `FunctionEnter2`</span><span class="sxs-lookup"><span data-stu-id="6ad99-123">A `COR_PRF_FRAME_INFO` that was obtained from a source other than a `FunctionEnter2` callback</span></span>|<span data-ttu-id="6ad99-124">Nelze určit přesný `ClassID` a argumenty typu.</span><span class="sxs-lookup"><span data-stu-id="6ad99-124">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="6ad99-125">To znamená, že `ClassID` může mít hodnotu null a některé argumenty typu se mohou vrátit jako <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="6ad99-125">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
|<span data-ttu-id="6ad99-126">Nula</span><span class="sxs-lookup"><span data-stu-id="6ad99-126">Zero</span></span>|<span data-ttu-id="6ad99-127">Nelze určit přesný `ClassID` a argumenty typu.</span><span class="sxs-lookup"><span data-stu-id="6ad99-127">The exact `ClassID` and type arguments cannot be determined.</span></span> <span data-ttu-id="6ad99-128">To znamená, že `ClassID` může mít hodnotu null a některé argumenty typu se mohou vrátit jako <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="6ad99-128">That is, the `ClassID` might be null and some type arguments might come back as <xref:System.Object>.</span></span>|  
  
 <span data-ttu-id="6ad99-129">Jakmile `GetFunctionInfo2` vrátí, je nutné ověřit, zda byla vyrovnávací paměť `typeArgs` dostatečně velká, aby obsahovala všechny `ClassID` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6ad99-129">After `GetFunctionInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="6ad99-130">To provedete tak, že porovnáte hodnotu, na kterou `pcTypeArgs` odkazuje, hodnotou `cTypeArgs` parametru.</span><span class="sxs-lookup"><span data-stu-id="6ad99-130">To do this, compare the value that `pcTypeArgs` points to with the value of the `cTypeArgs` parameter.</span></span> <span data-ttu-id="6ad99-131">Pokud `pcTypeArgs` odkazuje na hodnotu, která je větší než `cTypeArgs` dělená velikostí `ClassID` hodnoty, přidělte větší vyrovnávací paměť `pcTypeArgs`, aktualizujte `cTypeArgs` o novou, větší velikost a zavolejte `GetFunctionInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="6ad99-131">If `pcTypeArgs` points to a value that is larger than `cTypeArgs` divided by the size of a `ClassID` value, allocate a larger `pcTypeArgs` buffer, update `cTypeArgs` with the new, larger size, and call `GetFunctionInfo2` again.</span></span>  
  
 <span data-ttu-id="6ad99-132">Alternativně můžete pro získání správné velikosti vyrovnávací paměti nejprve volat `GetFunctionInfo2` s nulovou délkou `pcTypeArgs` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="6ad99-132">Alternatively, you can first call `GetFunctionInfo2` with a zero-length `pcTypeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="6ad99-133">Velikost vyrovnávací paměti pak můžete nastavit na hodnotu vrácenou v `pcTypeArgs` dělenou velikostí `ClassID` a volat `GetFunctionInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="6ad99-133">You can then set the buffer size to the value returned in `pcTypeArgs` divided by the size of a `ClassID` value, and call `GetFunctionInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ad99-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6ad99-134">Requirements</span></span>  
 <span data-ttu-id="6ad99-135">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ad99-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ad99-136">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6ad99-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6ad99-137">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6ad99-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ad99-138">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ad99-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ad99-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ad99-139">See also</span></span>

- [<span data-ttu-id="6ad99-140">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6ad99-140">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="6ad99-141">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6ad99-141">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="6ad99-142">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="6ad99-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="6ad99-143">Profilace</span><span class="sxs-lookup"><span data-stu-id="6ad99-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
