---
title: 'ICorDebugSymbolProvider2:: GetGenericDictionaryInfo – metoda'
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
ms.openlocfilehash: c9f7206cac54d64c28eb50d81fea00a6f3c494d4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133636"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a><span data-ttu-id="a3c31-102">ICorDebugSymbolProvider2:: GetGenericDictionaryInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="a3c31-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method</span></span>

<span data-ttu-id="a3c31-103">Načte mapu obecného slovníku.</span><span class="sxs-lookup"><span data-stu-id="a3c31-103">Retrieves a generic dictionary map.</span></span>

## <a name="syntax"></a><span data-ttu-id="a3c31-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3c31-104">Syntax</span></span>

```cpp
HRESULT GetGenericDictionaryInfo(
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer
);
```

## <a name="parameters"></a><span data-ttu-id="a3c31-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3c31-105">Parameters</span></span>

`ppMemoryBuffer`\
<span data-ttu-id="a3c31-106">mimo Ukazatel na adresu objektu [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) obsahující mapu obecného slovníku.</span><span class="sxs-lookup"><span data-stu-id="a3c31-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object containing the generic dictionary map.</span></span> <span data-ttu-id="a3c31-107">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="a3c31-107">See the Remarks section for more information.</span></span>

## <a name="remarks"></a><span data-ttu-id="a3c31-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a3c31-108">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="a3c31-109">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a3c31-109">This method is available with .NET Native only.</span></span>

<span data-ttu-id="a3c31-110">Mapa se skládá ze dvou sekcí nejvyšší úrovně:</span><span class="sxs-lookup"><span data-stu-id="a3c31-110">The map consists of two top-level sections:</span></span>

- <span data-ttu-id="a3c31-111">[Adresář](#Directory) obsahující relativní virtuální adresy (RVA) všech slovníků obsažených v této mapě.</span><span class="sxs-lookup"><span data-stu-id="a3c31-111">A [directory](#Directory) containing the relative virtual addresses (RVA) of all dictionaries included in this map.</span></span>

- <span data-ttu-id="a3c31-112">[Halda](#Heap) zarovnaná na bajt, která obsahuje informace o vytváření instancí objektů.</span><span class="sxs-lookup"><span data-stu-id="a3c31-112">A byte-aligned [heap](#Heap) that contains object instantiation information.</span></span> <span data-ttu-id="a3c31-113">Spustí se hned za poslední položkou adresáře.</span><span class="sxs-lookup"><span data-stu-id="a3c31-113">It starts immediately after the last directory entry.</span></span>

<a name="Directory"></a>

## <a name="the-directory"></a><span data-ttu-id="a3c31-114">Adresář</span><span class="sxs-lookup"><span data-stu-id="a3c31-114">The Directory</span></span>

<span data-ttu-id="a3c31-115">Každá položka v adresáři odkazuje na posun uvnitř haldy. To znamená, že se jedná o posun, který je relativní ke spuštění haldy.</span><span class="sxs-lookup"><span data-stu-id="a3c31-115">Each entry in the directory refers to an offset inside the heap; that is, it is an offset that is relative to the start of the heap.</span></span> <span data-ttu-id="a3c31-116">Hodnota jednotlivých položek není nutně jedinečná; je možné, aby více položek adresáře odkazovalo na stejný posun v haldě.</span><span class="sxs-lookup"><span data-stu-id="a3c31-116">The value of individual entries is not necessarily unique; it is possible for multiple directory entries to point to the same offset in the heap.</span></span>

<span data-ttu-id="a3c31-117">Část adresáře mapy obecného slovníku má následující strukturu:</span><span class="sxs-lookup"><span data-stu-id="a3c31-117">The directory portion of the generic dictionary map has the following structure:</span></span>

- <span data-ttu-id="a3c31-118">Prvních 4 bajtů obsahuje počet položek slovníku (tj. počet relativních virtuálních adres ve slovníku).</span><span class="sxs-lookup"><span data-stu-id="a3c31-118">The first 4 bytes contains the number of dictionary entries (that is, the number of relative virtual addresses in the dictionary).</span></span> <span data-ttu-id="a3c31-119">Na tuto hodnotu odkazujeme jako na *N*. Pokud je nastavený vysoký bit, položky se seřadí podle relativní virtuální adresy ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="a3c31-119">We will refer to this value as *N*. If the high bit is set, the entries are sorted by relative virtual address in ascending order.</span></span>

- <span data-ttu-id="a3c31-120">Následují položky adresáře *N* .</span><span class="sxs-lookup"><span data-stu-id="a3c31-120">The *N* directory entries follow.</span></span> <span data-ttu-id="a3c31-121">Každá položka se skládá z 8 bajtů, ve dvou segmentech se 4 bajty:</span><span class="sxs-lookup"><span data-stu-id="a3c31-121">Each entry consists of 8 bytes, in two 4-byte segments:</span></span>

  - <span data-ttu-id="a3c31-122">Bajty 0-3: RVA; relativní virtuální adresa slovníku</span><span class="sxs-lookup"><span data-stu-id="a3c31-122">Bytes 0-3: RVA; the dictionary's relative virtual address.</span></span>

  - <span data-ttu-id="a3c31-123">Bajty 4-7: offset; posun vzhledem k začátku haldy.</span><span class="sxs-lookup"><span data-stu-id="a3c31-123">Bytes 4-7: Offset; an offset relative to the start of the heap.</span></span>

<a name="Heap"></a>

## <a name="the-heap"></a><span data-ttu-id="a3c31-124">Halda</span><span class="sxs-lookup"><span data-stu-id="a3c31-124">The Heap</span></span>

<span data-ttu-id="a3c31-125">Velikost haldy lze vypočítat pomocí čtečky datového proudu odečtením délky datového proudu od velikosti adresáře + 4.</span><span class="sxs-lookup"><span data-stu-id="a3c31-125">The heap’s size can be computed by a stream reader by subtracting the length of the stream from the directory size + 4.</span></span> <span data-ttu-id="a3c31-126">Jinými slovy:</span><span class="sxs-lookup"><span data-stu-id="a3c31-126">In other words:</span></span>

```csharp
Heap Size = Stream.Length – (Directory Size + 4)
```

<span data-ttu-id="a3c31-127">kde je velikost adresáře `N * 8`.</span><span class="sxs-lookup"><span data-stu-id="a3c31-127">where the directory size is `N * 8`.</span></span>

<span data-ttu-id="a3c31-128">Formát pro každou položku informací o instanciaci haldy je:</span><span class="sxs-lookup"><span data-stu-id="a3c31-128">The format for each instantiation information item on the heap is:</span></span>

- <span data-ttu-id="a3c31-129">Délka položky informací o instanciování v bajtech v komprimovaném formátu metadat ECMA</span><span class="sxs-lookup"><span data-stu-id="a3c31-129">The length of this instantiation information item in bytes in compressed ECMA metadata format.</span></span> <span data-ttu-id="a3c31-130">Tato hodnota vylučuje tyto informace o délce.</span><span class="sxs-lookup"><span data-stu-id="a3c31-130">The value excludes this length information.</span></span>

- <span data-ttu-id="a3c31-131">Počet generických typů vytváření instancí, nebo *T*, v komprimovaném formátu metadat ECMA.</span><span class="sxs-lookup"><span data-stu-id="a3c31-131">The number of generic instantiation types, or *T*, in compressed ECMA metadata format.</span></span>

- <span data-ttu-id="a3c31-132">Typy *T* , z nichž každá představuje formát podpisu typu ECMA.</span><span class="sxs-lookup"><span data-stu-id="a3c31-132">*T* types, each represented in ECMA type signature format.</span></span>

<span data-ttu-id="a3c31-133">Zahrnutí délky pro každý prvek haldy umožňuje jednoduché řazení oddílu adresáře bez ovlivnění haldy.</span><span class="sxs-lookup"><span data-stu-id="a3c31-133">The inclusion of the length for each heap element enables simple sorting of the directory section without affecting the heap.</span></span>

## <a name="requirements"></a><span data-ttu-id="a3c31-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a3c31-134">Requirements</span></span>

<span data-ttu-id="a3c31-135">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3c31-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="a3c31-136">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a3c31-136">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="a3c31-137">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a3c31-137">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="a3c31-138">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3c31-138">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a3c31-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3c31-139">See also</span></span>

- [<span data-ttu-id="a3c31-140">ICorDebugSymbolProvider2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a3c31-140">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="a3c31-141">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a3c31-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
