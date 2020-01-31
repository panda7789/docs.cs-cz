---
title: ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
ms.openlocfilehash: 02ecaf56e845680472f42c04f3978e54e7a69272
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791498"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a><span data-ttu-id="87cc5-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method</span><span class="sxs-lookup"><span data-stu-id="87cc5-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method</span></span>

<span data-ttu-id="87cc5-103">Načte mapu obecného slovníku.</span><span class="sxs-lookup"><span data-stu-id="87cc5-103">Retrieves a generic dictionary map.</span></span>

## <a name="syntax"></a><span data-ttu-id="87cc5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87cc5-104">Syntax</span></span>

```cpp
HRESULT GetGenericDictionaryInfo(
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer
);
```

## <a name="parameters"></a><span data-ttu-id="87cc5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="87cc5-105">Parameters</span></span>

`ppMemoryBuffer`\
<span data-ttu-id="87cc5-106">mimo Ukazatel na adresu objektu [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) obsahující mapu obecného slovníku.</span><span class="sxs-lookup"><span data-stu-id="87cc5-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object containing the generic dictionary map.</span></span> <span data-ttu-id="87cc5-107">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="87cc5-107">See the Remarks section for more information.</span></span>

## <a name="remarks"></a><span data-ttu-id="87cc5-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="87cc5-108">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="87cc5-109">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="87cc5-109">This method is available with .NET Native only.</span></span>

<span data-ttu-id="87cc5-110">Mapa se skládá ze dvou sekcí nejvyšší úrovně:</span><span class="sxs-lookup"><span data-stu-id="87cc5-110">The map consists of two top-level sections:</span></span>

- <span data-ttu-id="87cc5-111">[Adresář](#Directory) obsahující relativní virtuální adresy (RVA) všech slovníků obsažených v této mapě.</span><span class="sxs-lookup"><span data-stu-id="87cc5-111">A [directory](#Directory) containing the relative virtual addresses (RVA) of all dictionaries included in this map.</span></span>

- <span data-ttu-id="87cc5-112">[Halda](#Heap) zarovnaná na bajt, která obsahuje informace o vytváření instancí objektů.</span><span class="sxs-lookup"><span data-stu-id="87cc5-112">A byte-aligned [heap](#Heap) that contains object instantiation information.</span></span> <span data-ttu-id="87cc5-113">Spustí se hned za poslední položkou adresáře.</span><span class="sxs-lookup"><span data-stu-id="87cc5-113">It starts immediately after the last directory entry.</span></span>

<a name="Directory"></a>

## <a name="the-directory"></a><span data-ttu-id="87cc5-114">Adresář</span><span class="sxs-lookup"><span data-stu-id="87cc5-114">The Directory</span></span>

<span data-ttu-id="87cc5-115">Každá položka v adresáři odkazuje na posun uvnitř haldy. To znamená, že se jedná o posun, který je relativní ke spuštění haldy.</span><span class="sxs-lookup"><span data-stu-id="87cc5-115">Each entry in the directory refers to an offset inside the heap; that is, it is an offset that is relative to the start of the heap.</span></span> <span data-ttu-id="87cc5-116">Hodnota jednotlivých položek není nutně jedinečná; je možné, aby více položek adresáře odkazovalo na stejný posun v haldě.</span><span class="sxs-lookup"><span data-stu-id="87cc5-116">The value of individual entries is not necessarily unique; it is possible for multiple directory entries to point to the same offset in the heap.</span></span>

<span data-ttu-id="87cc5-117">Část adresáře mapy obecného slovníku má následující strukturu:</span><span class="sxs-lookup"><span data-stu-id="87cc5-117">The directory portion of the generic dictionary map has the following structure:</span></span>

- <span data-ttu-id="87cc5-118">Prvních 4 bajtů obsahuje počet položek slovníku (tj. počet relativních virtuálních adres ve slovníku).</span><span class="sxs-lookup"><span data-stu-id="87cc5-118">The first 4 bytes contains the number of dictionary entries (that is, the number of relative virtual addresses in the dictionary).</span></span> <span data-ttu-id="87cc5-119">Na tuto hodnotu odkazujeme jako na *N*. Pokud je nastavený vysoký bit, položky se seřadí podle relativní virtuální adresy ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="87cc5-119">We will refer to this value as *N*. If the high bit is set, the entries are sorted by relative virtual address in ascending order.</span></span>

- <span data-ttu-id="87cc5-120">Následují položky adresáře *N* .</span><span class="sxs-lookup"><span data-stu-id="87cc5-120">The *N* directory entries follow.</span></span> <span data-ttu-id="87cc5-121">Každá položka se skládá z 8 bajtů, ve dvou segmentech se 4 bajty:</span><span class="sxs-lookup"><span data-stu-id="87cc5-121">Each entry consists of 8 bytes, in two 4-byte segments:</span></span>

  - <span data-ttu-id="87cc5-122">Bajty 0-3: RVA; relativní virtuální adresa slovníku</span><span class="sxs-lookup"><span data-stu-id="87cc5-122">Bytes 0-3: RVA; the dictionary's relative virtual address.</span></span>

  - <span data-ttu-id="87cc5-123">Bajty 4-7: offset; posun vzhledem k začátku haldy.</span><span class="sxs-lookup"><span data-stu-id="87cc5-123">Bytes 4-7: Offset; an offset relative to the start of the heap.</span></span>

<a name="Heap"></a>

## <a name="the-heap"></a><span data-ttu-id="87cc5-124">Halda</span><span class="sxs-lookup"><span data-stu-id="87cc5-124">The Heap</span></span>

<span data-ttu-id="87cc5-125">Velikost haldy lze vypočítat pomocí čtečky datového proudu odečtením délky datového proudu od velikosti adresáře + 4.</span><span class="sxs-lookup"><span data-stu-id="87cc5-125">The heap’s size can be computed by a stream reader by subtracting the length of the stream from the directory size + 4.</span></span> <span data-ttu-id="87cc5-126">Jinými slovy:</span><span class="sxs-lookup"><span data-stu-id="87cc5-126">In other words:</span></span>

```csharp
Heap Size = Stream.Length – (Directory Size + 4)
```

<span data-ttu-id="87cc5-127">kde je velikost adresáře `N * 8`.</span><span class="sxs-lookup"><span data-stu-id="87cc5-127">where the directory size is `N * 8`.</span></span>

<span data-ttu-id="87cc5-128">Formát pro každou položku informací o instanciaci haldy je:</span><span class="sxs-lookup"><span data-stu-id="87cc5-128">The format for each instantiation information item on the heap is:</span></span>

- <span data-ttu-id="87cc5-129">Délka položky informací o instanciování v bajtech v komprimovaném formátu metadat ECMA</span><span class="sxs-lookup"><span data-stu-id="87cc5-129">The length of this instantiation information item in bytes in compressed ECMA metadata format.</span></span> <span data-ttu-id="87cc5-130">Tato hodnota vylučuje tyto informace o délce.</span><span class="sxs-lookup"><span data-stu-id="87cc5-130">The value excludes this length information.</span></span>

- <span data-ttu-id="87cc5-131">Počet generických typů vytváření instancí, nebo *T*, v komprimovaném formátu metadat ECMA.</span><span class="sxs-lookup"><span data-stu-id="87cc5-131">The number of generic instantiation types, or *T*, in compressed ECMA metadata format.</span></span>

- <span data-ttu-id="87cc5-132">Typy *T* , z nichž každá představuje formát podpisu typu ECMA.</span><span class="sxs-lookup"><span data-stu-id="87cc5-132">*T* types, each represented in ECMA type signature format.</span></span>

<span data-ttu-id="87cc5-133">Zahrnutí délky pro každý prvek haldy umožňuje jednoduché řazení oddílu adresáře bez ovlivnění haldy.</span><span class="sxs-lookup"><span data-stu-id="87cc5-133">The inclusion of the length for each heap element enables simple sorting of the directory section without affecting the heap.</span></span>

## <a name="requirements"></a><span data-ttu-id="87cc5-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="87cc5-134">Requirements</span></span>

<span data-ttu-id="87cc5-135">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87cc5-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="87cc5-136">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="87cc5-136">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="87cc5-137">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="87cc5-137">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="87cc5-138">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87cc5-138">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="87cc5-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87cc5-139">See also</span></span>

- [<span data-ttu-id="87cc5-140">ICorDebugSymbolProvider2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87cc5-140">ICorDebugSymbolProvider2 Interface</span></span>](icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="87cc5-141">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="87cc5-141">Debugging Interfaces</span></span>](debugging-interfaces.md)
