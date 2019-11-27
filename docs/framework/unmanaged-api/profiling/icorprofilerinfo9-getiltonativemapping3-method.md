---
title: ICorProfilerInfo9::GetILToNativeMapping3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetILToNativeMapping3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 1a5a259e6604d906e55166b3fcb770bc37d346c5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444732"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a><span data-ttu-id="dacfe-102">ICorProfilerInfo9:: GetILToNativeMapping3 – metoda</span><span class="sxs-lookup"><span data-stu-id="dacfe-102">ICorProfilerInfo9::GetILToNativeMapping3 Method</span></span>

<span data-ttu-id="dacfe-103">Vzhledem k počáteční adrese nativního kódu vrací nativní informace mapování IL pro tuto verzi zpracovaných kompilátorem JIT kódu.</span><span class="sxs-lookup"><span data-stu-id="dacfe-103">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span>

## <a name="syntax"></a><span data-ttu-id="dacfe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dacfe-104">Syntax</span></span>

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

#### <a name="parameters"></a><span data-ttu-id="dacfe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dacfe-105">Parameters</span></span>

`pNativeCodeStartAddress` \
<span data-ttu-id="dacfe-106">pro Ukazatel na začátek nativní funkce.</span><span class="sxs-lookup"><span data-stu-id="dacfe-106">[in] A pointer to the start of a native function.</span></span>

`cMap` \
<span data-ttu-id="dacfe-107">pro Maximální velikost `map` pole</span><span class="sxs-lookup"><span data-stu-id="dacfe-107">[in] The maximum size of the `map` array.</span></span>

`pcMap` \
<span data-ttu-id="dacfe-108">mimo Celkový počet dostupných COR_DEBUG_IL_TO_NATIVE_MAP struktur.</span><span class="sxs-lookup"><span data-stu-id="dacfe-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>

`map` \
<span data-ttu-id="dacfe-109">mimo Pole struktur [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) , z nichž každý Určuje posun.</span><span class="sxs-lookup"><span data-stu-id="dacfe-109">[out] An array of [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) structures, each of which specifies the offsets.</span></span> <span data-ttu-id="dacfe-110">Po návratu metody `GetILToNativeMapping3` bude `map` obsahovat některé nebo všechny `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="dacfe-110">After the `GetILToNativeMapping3` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>

## <a name="remarks"></a><span data-ttu-id="dacfe-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dacfe-111">Remarks</span></span>

<span data-ttu-id="dacfe-112">Pokud je povolená vrstvená kompilace, může mít metoda více než jeden tělo nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="dacfe-112">When tiered compilation is enabled, a method may have more than one native code body.</span></span> <span data-ttu-id="dacfe-113">[ICorProfilerInfo9:: GetNativeCodeStartAddresses](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md) vrátí počáteční adresy pro všechny tělo nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="dacfe-113">[ICorProfilerInfo9::GetNativeCodeStartAddresses](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md) will return the start addresses for all of the native code bodies.</span></span>

## <a name="requirements"></a><span data-ttu-id="dacfe-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dacfe-114">Requirements</span></span>

<span data-ttu-id="dacfe-115">**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="dacfe-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="dacfe-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="dacfe-116">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="dacfe-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dacfe-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="dacfe-118">**Verze .NET Framework:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dacfe-118">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="dacfe-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dacfe-119">See also</span></span>

- [<span data-ttu-id="dacfe-120">Rozhraní ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="dacfe-120">ICorProfilerInfo9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)
