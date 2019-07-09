---
title: ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65407fca73971546725d9457d25bf1270d2001e2
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662538"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a><span data-ttu-id="35e21-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method</span><span class="sxs-lookup"><span data-stu-id="35e21-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method</span></span>

<span data-ttu-id="35e21-103">Načte mapování generický slovník.</span><span class="sxs-lookup"><span data-stu-id="35e21-103">Retrieves a generic dictionary map.</span></span>

## <a name="syntax"></a><span data-ttu-id="35e21-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35e21-104">Syntax</span></span>

```cpp
HRESULT GetGenericDictionaryInfo(
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer
);
```

## <a name="parameters"></a><span data-ttu-id="35e21-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="35e21-105">Parameters</span></span>

`ppMemoryBuffer`\
<span data-ttu-id="35e21-106">[out] Ukazatel na adresu [icordebugmemorybuffer –](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objekt, který obsahuje generický slovník mapování.</span><span class="sxs-lookup"><span data-stu-id="35e21-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object containing the generic dictionary map.</span></span> <span data-ttu-id="35e21-107">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="35e21-107">See the Remarks section for more information.</span></span>

## <a name="remarks"></a><span data-ttu-id="35e21-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="35e21-108">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="35e21-109">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="35e21-109">This method is available with .NET Native only.</span></span>

<span data-ttu-id="35e21-110">Mapa se skládá ze dvou částí nejvyšší úrovně:</span><span class="sxs-lookup"><span data-stu-id="35e21-110">The map consists of two top-level sections:</span></span>

- <span data-ttu-id="35e21-111">A [directory](#Directory) relativních virtuálních adres (RVA) obsahující všechny adresářů, které jsou součástí této mapy.</span><span class="sxs-lookup"><span data-stu-id="35e21-111">A [directory](#Directory) containing the relative virtual addresses (RVA) of all dictionaries included in this map.</span></span>

- <span data-ttu-id="35e21-112">Zarovnané bajtové [haldy](#Heap) , který obsahuje informace o vytvoření instance objektu.</span><span class="sxs-lookup"><span data-stu-id="35e21-112">A byte-aligned [heap](#Heap) that contains object instantiation information.</span></span> <span data-ttu-id="35e21-113">Začne okamžitě po poslední položky adresáře.</span><span class="sxs-lookup"><span data-stu-id="35e21-113">It starts immediately after the last directory entry.</span></span>

<a name="Directory"></a>

## <a name="the-directory"></a><span data-ttu-id="35e21-114">Adresář</span><span class="sxs-lookup"><span data-stu-id="35e21-114">The Directory</span></span>

<span data-ttu-id="35e21-115">Každá položka v adresáři odkazuje na posun uvnitř haldy; To znamená je posunu, který je relativní vzhledem k začátku haldy.</span><span class="sxs-lookup"><span data-stu-id="35e21-115">Each entry in the directory refers to an offset inside the heap; that is, it is an offset that is relative to the start of the heap.</span></span> <span data-ttu-id="35e21-116">Hodnota jednotlivých položek, které není nutně jedinečné; je možné pro více položek adresáře tak, aby odkazoval na stejný posun v haldě.</span><span class="sxs-lookup"><span data-stu-id="35e21-116">The value of individual entries is not necessarily unique; it is possible for multiple directory entries to point to the same offset in the heap.</span></span>

<span data-ttu-id="35e21-117">Část adresáře generický slovník mapování má následující strukturu:</span><span class="sxs-lookup"><span data-stu-id="35e21-117">The directory portion of the generic dictionary map has the following structure:</span></span>

- <span data-ttu-id="35e21-118">První 4 bajty obsahuje počet položek slovníku (to znamená, že počet relativních virtuálních adres ve slovníku).</span><span class="sxs-lookup"><span data-stu-id="35e21-118">The first 4 bytes contains the number of dictionary entries (that is, the number of relative virtual addresses in the dictionary).</span></span> <span data-ttu-id="35e21-119">Společnost Microsoft bude odkazovat na tuto hodnotu jako *N*. Pokud je vysoký bit nastaven, jsou položky seřazené podle relativní virtuální adresa ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="35e21-119">We will refer to this value as *N*. If the high bit is set, the entries are sorted by relative virtual address in ascending order.</span></span>

- <span data-ttu-id="35e21-120">*N* postupujte podle položek adresáře.</span><span class="sxs-lookup"><span data-stu-id="35e21-120">The *N* directory entries follow.</span></span> <span data-ttu-id="35e21-121">Každý záznam se skládá z 8 bajtů v dva segmenty 4bajtovou:</span><span class="sxs-lookup"><span data-stu-id="35e21-121">Each entry consists of 8 bytes, in two 4-byte segments:</span></span>

  - <span data-ttu-id="35e21-122">Bajty 0 až 3: ADRESA RVA; relativní virtuální adresu do slovníku.</span><span class="sxs-lookup"><span data-stu-id="35e21-122">Bytes 0-3: RVA; the dictionary's relative virtual address.</span></span>

  - <span data-ttu-id="35e21-123">Bajty 4 – 7: Posun; posun vzhledem k začátku haldy.</span><span class="sxs-lookup"><span data-stu-id="35e21-123">Bytes 4-7: Offset; an offset relative to the start of the heap.</span></span>

<a name="Heap"></a>

## <a name="the-heap"></a><span data-ttu-id="35e21-124">Haldy</span><span class="sxs-lookup"><span data-stu-id="35e21-124">The Heap</span></span>

<span data-ttu-id="35e21-125">Velikost haldy můžete vypočítat čtečka stream tak, že se délka datového proudu z velikosti adresářů a 4.</span><span class="sxs-lookup"><span data-stu-id="35e21-125">The heap’s size can be computed by a stream reader by subtracting the length of the stream from the directory size + 4.</span></span> <span data-ttu-id="35e21-126">Jinými slovy:</span><span class="sxs-lookup"><span data-stu-id="35e21-126">In other words:</span></span>

```csharp
Heap Size = Stream.Length – (Directory Size + 4)
```

<span data-ttu-id="35e21-127">kde je velikost adresáře `N * 8`.</span><span class="sxs-lookup"><span data-stu-id="35e21-127">where the directory size is `N * 8`.</span></span>

<span data-ttu-id="35e21-128">Formát pro každou položku informace o vytvoření instance na haldě je:</span><span class="sxs-lookup"><span data-stu-id="35e21-128">The format for each instantiation information item on the heap is:</span></span>

- <span data-ttu-id="35e21-129">Délka této položky informace o vytvoření instance v bajtech ve formátu metadat komprimované ECMA.</span><span class="sxs-lookup"><span data-stu-id="35e21-129">The length of this instantiation information item in bytes in compressed ECMA metadata format.</span></span> <span data-ttu-id="35e21-130">Hodnota nezahrnuje informace o délce.</span><span class="sxs-lookup"><span data-stu-id="35e21-130">The value excludes this length information.</span></span>

- <span data-ttu-id="35e21-131">Počet typů obecné vytváření instancí, nebo *T*, v komprimované formát metadat ECMA.</span><span class="sxs-lookup"><span data-stu-id="35e21-131">The number of generic instantiation types, or *T*, in compressed ECMA metadata format.</span></span>

- <span data-ttu-id="35e21-132">*T* typy, znázorněny ve formátu podpisu typu ECMA.</span><span class="sxs-lookup"><span data-stu-id="35e21-132">*T* types, each represented in ECMA type signature format.</span></span>

<span data-ttu-id="35e21-133">Zahrnutí délka pro každý prvek haldy umožňuje jednoduché řazení sekci adresáře aniž by to ovlivnilo haldy.</span><span class="sxs-lookup"><span data-stu-id="35e21-133">The inclusion of the length for each heap element enables simple sorting of the directory section without affecting the heap.</span></span>

## <a name="requirements"></a><span data-ttu-id="35e21-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="35e21-134">Requirements</span></span>

<span data-ttu-id="35e21-135">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35e21-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="35e21-136">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="35e21-136">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="35e21-137">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35e21-137">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="35e21-138">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35e21-138">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="35e21-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="35e21-139">See also</span></span>

- [<span data-ttu-id="35e21-140">ICorDebugSymbolProvider2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="35e21-140">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="35e21-141">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="35e21-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
