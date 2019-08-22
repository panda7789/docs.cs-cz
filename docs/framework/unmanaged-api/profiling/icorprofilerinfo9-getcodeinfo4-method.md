---
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: e6708971909c1035e41786f4d8dad1cf9afdffaf
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665618"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a><span data-ttu-id="e06cb-102">ICorProfilerInfo9:: GetCodeInfo4 – metoda</span><span class="sxs-lookup"><span data-stu-id="e06cb-102">ICorProfilerInfo9::GetCodeInfo4 Method</span></span>

<span data-ttu-id="e06cb-103">Vzhledem k počáteční adrese nativního kódu vrátí bloky virtuální paměti, která ukládá tento kód.</span><span class="sxs-lookup"><span data-stu-id="e06cb-103">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span>

## <a name="syntax"></a><span data-ttu-id="e06cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e06cb-104">Syntax</span></span>

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

#### <a name="parameters"></a><span data-ttu-id="e06cb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e06cb-105">Parameters</span></span>

`pNativeCodeStartAddress` \
<span data-ttu-id="e06cb-106">pro Ukazatel na začátek nativní funkce.</span><span class="sxs-lookup"><span data-stu-id="e06cb-106">[in] A pointer to the start of a native function.</span></span>

`cCodeInfos` \
<span data-ttu-id="e06cb-107">pro Velikost `codeInfos` pole.</span><span class="sxs-lookup"><span data-stu-id="e06cb-107">[in] The size of the `codeInfos` array.</span></span>

`pcCodeInfos` \
<span data-ttu-id="e06cb-108">mimo Ukazatel na celkový počet dostupných struktur [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)</span><span class="sxs-lookup"><span data-stu-id="e06cb-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>

`codeInfos` \
<span data-ttu-id="e06cb-109">mimo Vyrovnávací paměť poskytnutá volajícím.</span><span class="sxs-lookup"><span data-stu-id="e06cb-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="e06cb-110">Poté, co metoda vrátí, obsahuje pole `COR_PRF_CODE_INFO` struktury, z nichž každý popisuje blok nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="e06cb-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e06cb-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e06cb-111">Remarks</span></span>

<span data-ttu-id="e06cb-112">Metoda je podobná GetCodeInfo3 –, s tím rozdílem, že může vyhledat informace o kódu pro různé nativní verze metody. [](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md) `GetCodeInfo4`</span><span class="sxs-lookup"><span data-stu-id="e06cb-112">The `GetCodeInfo4` method is similar to [GetCodeInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md), except that it can look up code information for different native versions of a method.</span></span>

> [!NOTE]
> <span data-ttu-id="e06cb-113">`GetCodeInfo4`může aktivovat uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="e06cb-113">`GetCodeInfo4` can trigger a garbage collection.</span></span>

<span data-ttu-id="e06cb-114">Rozsahy jsou seřazené v pořadí zvyšování Common Intermediate Language (CIL) posun.</span><span class="sxs-lookup"><span data-stu-id="e06cb-114">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>

<span data-ttu-id="e06cb-115">Po `GetCodeInfo4` návratu je nutné ověřit `codeInfos` , zda byla vyrovnávací paměť dostatečně velká, aby obsahovala všechny struktury [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="e06cb-115">After `GetCodeInfo4` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="e06cb-116">Chcete-li to provést, porovnejte `cCodeInfos` hodnotu s hodnotou `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="e06cb-116">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="e06cb-117">Je `cCodeInfos` -li děleno velikostí struktury [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) menší než `pcCodeInfos`, přidělte větší `codeInfos` vyrovnávací paměť, aktualizujte `cCodeInfos` novou, větší velikost a zavolejte `GetCodeInfo4` znovu.</span><span class="sxs-lookup"><span data-stu-id="e06cb-117">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo4` again.</span></span>

<span data-ttu-id="e06cb-118">Případně můžete pro získání správné velikosti `GetCodeInfo4` vyrovnávací paměti nejprve zavolat s `codeInfos` nulovou délkou vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e06cb-118">Alternatively, you can first call `GetCodeInfo4` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="e06cb-119">Pak můžete `codeInfos` nastavit velikost vyrovnávací paměti na hodnotu vrácenou `pcCodeInfos`v, vynásobenou velikostí [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury a volat `GetCodeInfo4` znovu.</span><span class="sxs-lookup"><span data-stu-id="e06cb-119">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure, and call `GetCodeInfo4` again.</span></span>

## <a name="requirements"></a><span data-ttu-id="e06cb-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e06cb-120">Requirements</span></span>

<span data-ttu-id="e06cb-121">**Platformu** Viz [podporované operační systémy .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="e06cb-121">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="e06cb-122">**Hlaviček** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e06cb-122">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="e06cb-123">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e06cb-123">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="e06cb-124">**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e06cb-124">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e06cb-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e06cb-125">See also</span></span>

- [<span data-ttu-id="e06cb-126">Rozhraní ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="e06cb-126">ICorProfilerInfo9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/ICorProfilerInfo9-interface.md)
