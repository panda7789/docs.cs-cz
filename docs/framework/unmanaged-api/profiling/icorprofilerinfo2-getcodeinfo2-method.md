---
title: ICorProfilerInfo2::GetCodeInfo2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetCodeInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type:
- apiref
ms.openlocfilehash: 5149e3fab023de42d03673ec5d3e5ae888a9ed5a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433289"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a><span data-ttu-id="0c143-102">ICorProfilerInfo2::GetCodeInfo2 – metoda</span><span class="sxs-lookup"><span data-stu-id="0c143-102">ICorProfilerInfo2::GetCodeInfo2 Method</span></span>
<span data-ttu-id="0c143-103">Získá rozsahy nativního kódu přidruženého k zadané `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="0c143-103">Gets the extents of native code associated with the specified `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c143-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c143-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c143-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c143-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="0c143-106">pro ID funkce, ke které je přidružen nativní kód.</span><span class="sxs-lookup"><span data-stu-id="0c143-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="0c143-107">pro Velikost pole `codeInfos`.</span><span class="sxs-lookup"><span data-stu-id="0c143-107">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="0c143-108">mimo Ukazatel na celkový počet dostupných struktur [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="0c143-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="0c143-109">mimo Vyrovnávací paměť poskytnutá volajícím.</span><span class="sxs-lookup"><span data-stu-id="0c143-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="0c143-110">Poté, co metoda vrátí, obsahuje pole `COR_PRF_CODE_INFO` struktury, z nichž každý popisuje blok nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="0c143-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c143-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0c143-111">Remarks</span></span>  
 <span data-ttu-id="0c143-112">Rozsahy jsou seřazené v pořadí od zvýšení posunu jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="0c143-112">The extents are sorted in order of increasing Microsoft intermediate language (MSIL) offset.</span></span>  
  
 <span data-ttu-id="0c143-113">Po `GetCodeInfo2` vrátí, je nutné ověřit, zda byla vyrovnávací paměť `codeInfos` dostatečně velká, aby obsahovala všechny `COR_PRF_CODE_INFO` struktury.</span><span class="sxs-lookup"><span data-stu-id="0c143-113">After `GetCodeInfo2` returns, you must verify that the `codeInfos` buffer was large enough to contain all the `COR_PRF_CODE_INFO` structures.</span></span> <span data-ttu-id="0c143-114">To provedete tak, že porovnáte hodnotu `cCodeInfos` s hodnotou parametru `cchName`.</span><span class="sxs-lookup"><span data-stu-id="0c143-114">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="0c143-115">Pokud je `cCodeInfos` dělené velikostí `COR_PRF_CODE_INFO` struktury menší než `pcCodeInfos`, přidělte větší vyrovnávací paměť `codeInfos`, aktualizujte `cCodeInfos` o novou, větší velikost a zavolejte `GetCodeInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="0c143-115">If `cCodeInfos` divided by the size of a `COR_PRF_CODE_INFO` structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo2` again.</span></span>  
  
 <span data-ttu-id="0c143-116">Alternativně můžete pro získání správné velikosti vyrovnávací paměti nejprve volat `GetCodeInfo2` s nulovou délkou `codeInfos` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="0c143-116">Alternatively, you can first call `GetCodeInfo2` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="0c143-117">Pak můžete nastavit velikost vyrovnávací paměti `codeInfos` na hodnotu vrácenou v `pcCodeInfos`vynásobenou velikostí `COR_PRF_CODE_INFO` struktury a znovu volat `GetCodeInfo2`.</span><span class="sxs-lookup"><span data-stu-id="0c143-117">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a `COR_PRF_CODE_INFO` structure, and call `GetCodeInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c143-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0c143-118">Requirements</span></span>  
 <span data-ttu-id="0c143-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c143-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c143-120">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0c143-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0c143-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0c143-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c143-122">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c143-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c143-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c143-123">See also</span></span>

- [<span data-ttu-id="0c143-124">GetCodeInfo3 – metoda</span><span class="sxs-lookup"><span data-stu-id="0c143-124">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)
- [<span data-ttu-id="0c143-125">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c143-125">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="0c143-126">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="0c143-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="0c143-127">Profilace</span><span class="sxs-lookup"><span data-stu-id="0c143-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
