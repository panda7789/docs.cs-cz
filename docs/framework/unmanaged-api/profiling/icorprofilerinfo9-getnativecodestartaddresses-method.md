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
ms.openlocfilehash: 80571933bc8d91c074dbee62aad50cece6277d51
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665520"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a><span data-ttu-id="bd037-102">ICorProfilerInfo9:: GetNativeCodeStartAddresses – metoda</span><span class="sxs-lookup"><span data-stu-id="bd037-102">ICorProfilerInfo9::GetNativeCodeStartAddresses Method</span></span>

<span data-ttu-id="bd037-103">S ohledem na functionId a rejitId vytvoří výčet počáteční adresy kódu pro všechny zpracovaných kompilátorem JIT verze tohoto kódu, který aktuálně existuje.</span><span class="sxs-lookup"><span data-stu-id="bd037-103">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span>

## <a name="syntax"></a><span data-ttu-id="bd037-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd037-104">Syntax</span></span>

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

#### <a name="parameters"></a><span data-ttu-id="bd037-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd037-105">Parameters</span></span>

`functionId` \
<span data-ttu-id="bd037-106">pro Mělo by se vrátit ID funkce, jejíž počáteční adresy nativního kódu by měly být vráceny.</span><span class="sxs-lookup"><span data-stu-id="bd037-106">[in] The ID of the function whose native code start addresses should be returned.</span></span>

`reJitId` \
<span data-ttu-id="bd037-107">pro Identita funkce Rekompilované JIT.</span><span class="sxs-lookup"><span data-stu-id="bd037-107">[in] The identity of the JIT-recompiled function.</span></span>

`cCodeStartAddresses` \
<span data-ttu-id="bd037-108">pro Maximální velikost `codeStartAddresses` pole.</span><span class="sxs-lookup"><span data-stu-id="bd037-108">[in] The maximum size of the `codeStartAddresses` array.</span></span>

`pcCodeStartAddresses` \
<span data-ttu-id="bd037-109">mimo Počet dostupných adres.</span><span class="sxs-lookup"><span data-stu-id="bd037-109">[out] The number of available addresses.</span></span>

`codeStartAddresses` \
<span data-ttu-id="bd037-110">mimo Pole `UINT_PTR`, z nichž každá z nich je počáteční adresou pro nativní tělo zadané funkce.</span><span class="sxs-lookup"><span data-stu-id="bd037-110">[out] An array of `UINT_PTR`, each one of which is the start address for a native body for the specified function.</span></span>

## <a name="remarks"></a><span data-ttu-id="bd037-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bd037-111">Remarks</span></span>

<span data-ttu-id="bd037-112">Pokud je povolená vrstvená kompilace, funkce může mít více než jeden tělo nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="bd037-112">When tiered compilation is enabled, a function may have more than one native code body.</span></span>

## <a name="requirements"></a><span data-ttu-id="bd037-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bd037-113">Requirements</span></span>

<span data-ttu-id="bd037-114">**Platformu** Viz [podporované operační systémy .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="bd037-114">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="bd037-115">**Hlaviček** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bd037-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="bd037-116">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd037-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="bd037-117">**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd037-117">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bd037-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd037-118">See also</span></span>

- [<span data-ttu-id="bd037-119">Rozhraní ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="bd037-119">ICorProfilerInfo9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)
