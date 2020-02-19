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
ms.openlocfilehash: f65cebff912adeb7afc34434467cf7be72f9be32
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449761"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a><span data-ttu-id="794cd-102">ICorProfilerInfo9:: GetCodeInfo4 – metoda</span><span class="sxs-lookup"><span data-stu-id="794cd-102">ICorProfilerInfo9::GetCodeInfo4 Method</span></span>

<span data-ttu-id="794cd-103">Vzhledem k počáteční adrese nativního kódu vrátí bloky virtuální paměti, která ukládá tento kód.</span><span class="sxs-lookup"><span data-stu-id="794cd-103">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span>

## <a name="syntax"></a><span data-ttu-id="794cd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="794cd-104">Syntax</span></span>

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

## <a name="parameters"></a><span data-ttu-id="794cd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="794cd-105">Parameters</span></span>

- `pNativeCodeStartAddress`

  <span data-ttu-id="794cd-106">\[in] ukazatel na začátek nativní funkce.</span><span class="sxs-lookup"><span data-stu-id="794cd-106">\[in] A pointer to the start of a native function.</span></span>

- `cCodeInfos`

  <span data-ttu-id="794cd-107">\[] velikost pole `codeInfos`.</span><span class="sxs-lookup"><span data-stu-id="794cd-107">\[in] The size of the `codeInfos` array.</span></span>

- `pcCodeInfos`

  <span data-ttu-id="794cd-108">\[] ukazatel na celkový počet dostupných [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) struktur.</span><span class="sxs-lookup"><span data-stu-id="794cd-108">\[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>

- `codeInfos`

  <span data-ttu-id="794cd-109">\[] vyrovnávací paměť poskytnutou volajícím.</span><span class="sxs-lookup"><span data-stu-id="794cd-109">\[out] A caller-provided buffer.</span></span> <span data-ttu-id="794cd-110">Poté, co metoda vrátí, obsahuje pole `COR_PRF_CODE_INFO` struktury, z nichž každý popisuje blok nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="794cd-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>

## <a name="remarks"></a><span data-ttu-id="794cd-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="794cd-111">Remarks</span></span>

<span data-ttu-id="794cd-112">Metoda `GetCodeInfo4` je podobná [GetCodeInfo3 –](icorprofilerinfo4-getcodeinfo3-method.md), s tím rozdílem, že může vyhledat informace o kódu pro různé nativní verze metody.</span><span class="sxs-lookup"><span data-stu-id="794cd-112">The `GetCodeInfo4` method is similar to [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md), except that it can look up code information for different native versions of a method.</span></span>

> [!NOTE]
> <span data-ttu-id="794cd-113">`GetCodeInfo4` může aktivovat uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="794cd-113">`GetCodeInfo4` can trigger a garbage collection.</span></span>

<span data-ttu-id="794cd-114">Rozsahy jsou seřazené v pořadí zvyšování Common Intermediate Language (CIL) posun.</span><span class="sxs-lookup"><span data-stu-id="794cd-114">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>

<span data-ttu-id="794cd-115">Po `GetCodeInfo4` vrátí, je nutné ověřit, zda byla vyrovnávací paměť `codeInfos` dostatečně velká, aby obsahovala všechny [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="794cd-115">After `GetCodeInfo4` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="794cd-116">To provedete tak, že porovnáte hodnotu `cCodeInfos` s hodnotou parametru `cchName`.</span><span class="sxs-lookup"><span data-stu-id="794cd-116">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="794cd-117">Pokud je `cCodeInfos` dělené velikostí [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) struktury menší než `pcCodeInfos`, přidělte větší vyrovnávací paměť `codeInfos`, aktualizujte `cCodeInfos` o novou, větší velikost a zavolejte `GetCodeInfo4` znovu.</span><span class="sxs-lookup"><span data-stu-id="794cd-117">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo4` again.</span></span>

<span data-ttu-id="794cd-118">Alternativně můžete pro získání správné velikosti vyrovnávací paměti nejprve volat `GetCodeInfo4` s nulovou délkou `codeInfos` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="794cd-118">Alternatively, you can first call `GetCodeInfo4` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="794cd-119">Pak můžete nastavit velikost vyrovnávací paměti `codeInfos` na hodnotu vrácenou v `pcCodeInfos`vynásobenou velikostí [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) struktury a znovu volat `GetCodeInfo4`.</span><span class="sxs-lookup"><span data-stu-id="794cd-119">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure, and call `GetCodeInfo4` again.</span></span>

## <a name="requirements"></a><span data-ttu-id="794cd-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="794cd-120">Requirements</span></span>

<span data-ttu-id="794cd-121">**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="794cd-121">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="794cd-122">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="794cd-122">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="794cd-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="794cd-123">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="794cd-124">**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="794cd-124">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="794cd-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="794cd-125">See also</span></span>

- [<span data-ttu-id="794cd-126">Rozhraní ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="794cd-126">ICorProfilerInfo9 Interface</span></span>](ICorProfilerInfo9-interface.md)
