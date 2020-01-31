---
title: ICorProfilerInfo9::GetNativeCodeStartAddresses
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 8412020fb98fde245b873a2f0c6a355f6436f712
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868275"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a><span data-ttu-id="062a9-102">ICorProfilerInfo9:: GetNativeCodeStartAddresses – metoda</span><span class="sxs-lookup"><span data-stu-id="062a9-102">ICorProfilerInfo9::GetNativeCodeStartAddresses Method</span></span>

<span data-ttu-id="062a9-103">S ohledem na functionId a rejitId vytvoří výčet počáteční adresy kódu pro všechny zpracovaných kompilátorem JIT verze tohoto kódu, který aktuálně existuje.</span><span class="sxs-lookup"><span data-stu-id="062a9-103">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span>

## <a name="syntax"></a><span data-ttu-id="062a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="062a9-104">Syntax</span></span>

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a><span data-ttu-id="062a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="062a9-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="062a9-106">\[in] ID funkce, jejíž počáteční adresy nativního kódu by měly být vráceny.</span><span class="sxs-lookup"><span data-stu-id="062a9-106">\[in] The ID of the function whose native code start addresses should be returned.</span></span>

- `reJitId`

  <span data-ttu-id="062a9-107">\[in] identita funkce Rekompilované JIT.</span><span class="sxs-lookup"><span data-stu-id="062a9-107">\[in] The identity of the JIT-recompiled function.</span></span>

- `cCodeStartAddresses`

  <span data-ttu-id="062a9-108">\[v] maximální velikost pole `codeStartAddresses`.</span><span class="sxs-lookup"><span data-stu-id="062a9-108">\[in] The maximum size of the `codeStartAddresses` array.</span></span>

- `pcCodeStartAddresses`

  <span data-ttu-id="062a9-109">\[] počet dostupných adres.</span><span class="sxs-lookup"><span data-stu-id="062a9-109">\[out] The number of available addresses.</span></span>

- `codeStartAddresses`

  <span data-ttu-id="062a9-110">\[) pole `UINT_PTR`, z nichž každá z nich představuje počáteční adresu pro nativní tělo zadané funkce.</span><span class="sxs-lookup"><span data-stu-id="062a9-110">\[out] An array of `UINT_PTR`, each one of which is the start address for a native body for the specified function.</span></span>

## <a name="remarks"></a><span data-ttu-id="062a9-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="062a9-111">Remarks</span></span>

<span data-ttu-id="062a9-112">Pokud je povolená vrstvená kompilace, funkce může mít více než jeden tělo nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="062a9-112">When tiered compilation is enabled, a function may have more than one native code body.</span></span>

## <a name="requirements"></a><span data-ttu-id="062a9-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="062a9-113">Requirements</span></span>

<span data-ttu-id="062a9-114">**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="062a9-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="062a9-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="062a9-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="062a9-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="062a9-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="062a9-117">**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="062a9-117">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="062a9-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="062a9-118">See also</span></span>

- [<span data-ttu-id="062a9-119">Rozhraní ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="062a9-119">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
