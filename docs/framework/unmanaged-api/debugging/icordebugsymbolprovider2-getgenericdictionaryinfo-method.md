---
title: "ICorDebugSymbolProvider2::GetGenericDictionaryInfo – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63126e4f34ea7ea7dee7dd0b9cae0dc0fea57ed9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a><span data-ttu-id="c7d1b-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="c7d1b-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method</span></span>
<span data-ttu-id="c7d1b-103">Načte mapu obecné slovníku.</span><span class="sxs-lookup"><span data-stu-id="c7d1b-103">Retrieves a generic dictionary map.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7d1b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7d1b-104">Syntax</span></span>  
  
```  
HRESULT GetGenericDictionaryInfo(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7d1b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7d1b-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="c7d1b-106">[out] Ukazatel na adresu [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objekt obsahující obecné slovník mapy.</span><span class="sxs-lookup"><span data-stu-id="c7d1b-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object containing the generic dictionary map.</span></span> <span data-ttu-id="c7d1b-107">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="c7d1b-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7d1b-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c7d1b-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7d1b-109">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="c7d1b-109">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="c7d1b-110">Mapy se skládá ze dvou částech nejvyšší úrovně:</span><span class="sxs-lookup"><span data-stu-id="c7d1b-110">The map consists of two top-level sections:</span></span>  
  
-   <span data-ttu-id="c7d1b-111">A [directory](#Directory) obsahující všechny slovníků zahrnuté v této mapě relativní virtuální adresy (RVA).</span><span class="sxs-lookup"><span data-stu-id="c7d1b-111">A [directory](#Directory) containing the relative virtual addresses (RVA) of all dictionaries included in this map.</span></span>  
  
-   <span data-ttu-id="c7d1b-112">Zarovnaný bajtů [haldy](#Heap) obsahující informace o vytvoření instance objektu.</span><span class="sxs-lookup"><span data-stu-id="c7d1b-112">A byte-aligned [heap](#Heap) that contains object instantiation information.</span></span> <span data-ttu-id="c7d1b-113">Spustí ihned po poslední položky adresáře.</span><span class="sxs-lookup"><span data-stu-id="c7d1b-113">It starts immediately after the last directory entry.</span></span>  
  
<a name="Directory"></a>   
## <a name="the-directory"></a><span data-ttu-id="c7d1b-114">Adresář</span><span class="sxs-lookup"><span data-stu-id="c7d1b-114">The Directory</span></span>  
 <span data-ttu-id="c7d1b-115">Každá položka v adresáři odkazuje na posun v haldě; To znamená je posun, který je relativní vzhledem ke spuštění haldě.</span><span class="sxs-lookup"><span data-stu-id="c7d1b-115">Each entry in the directory refers to an offset inside the heap; that is, it is an offset that is relative to the start of the heap.</span></span> <span data-ttu-id="c7d1b-116">Hodnota jednotlivých položek není nutně jedinečný; je možné pro více položek adresáře tak, aby odkazoval na stejné posun v haldě.</span><span class="sxs-lookup"><span data-stu-id="c7d1b-116">The value of individual entries is not necessarily unique; it is possible for multiple directory entries to point to the same offset in the heap.</span></span>  
  
 <span data-ttu-id="c7d1b-117">Část directory mapy obecné slovník má následující strukturu:</span><span class="sxs-lookup"><span data-stu-id="c7d1b-117">The directory portion of the generic dictionary map has the following structure:</span></span>  
  
-   <span data-ttu-id="c7d1b-118">První 4 bajty obsahuje počet položky slovníku (to znamená, počet relativní virtuální adresy ve slovníku).</span><span class="sxs-lookup"><span data-stu-id="c7d1b-118">The first 4 bytes contains the number of dictionary entries (that is, the number of relative virtual addresses in the dictionary).</span></span> <span data-ttu-id="c7d1b-119">Budeme odkazovat na tuto hodnotu jako *N*. Pokud je nastavena rozšířené, jsou položky seřazené podle relativní virtuální adresy ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="c7d1b-119">We will refer to this value as *N*. If the high bit is set, the entries are sorted by relative virtual address in ascending order.</span></span>  
  
-   <span data-ttu-id="c7d1b-120">*N* podle položek adresáře.</span><span class="sxs-lookup"><span data-stu-id="c7d1b-120">The *N* directory entries follow.</span></span> <span data-ttu-id="c7d1b-121">Každý záznam se skládá z 8 bajtů v dva segmenty 4bajtový:</span><span class="sxs-lookup"><span data-stu-id="c7d1b-121">Each entry consists of 8 bytes, in two 4-byte segments:</span></span>  
  
    -   <span data-ttu-id="c7d1b-122">Bajty 0 až 3: RVA; relativní virtuální adresy slovníku.</span><span class="sxs-lookup"><span data-stu-id="c7d1b-122">Bytes 0-3: RVA; the dictionary's relative virtual address.</span></span>  
  
    -   <span data-ttu-id="c7d1b-123">Bajty 4-7: posun; posun vzhledem k začátku haldě.</span><span class="sxs-lookup"><span data-stu-id="c7d1b-123">Bytes 4-7: Offset; an offset relative to the start of the heap.</span></span>  
  
<a name="Heap"></a>   
## <a name="the-heap"></a><span data-ttu-id="c7d1b-124">Halda</span><span class="sxs-lookup"><span data-stu-id="c7d1b-124">The Heap</span></span>  
 <span data-ttu-id="c7d1b-125">Velikost haldy pro mocninou čtečku datového proudu odečtením délka datového proudu z adresáře velikost + 4.</span><span class="sxs-lookup"><span data-stu-id="c7d1b-125">The heap’s size can be computed by a stream reader by subtracting the length of the stream from the directory size + 4.</span></span> <span data-ttu-id="c7d1b-126">Jinými slovy:</span><span class="sxs-lookup"><span data-stu-id="c7d1b-126">In other words:</span></span>  
  
```  
Heap Size = Stream.Length – (Directory Size + 4)  
```  
  
 <span data-ttu-id="c7d1b-127">kde je velikost directory `N * 8`.</span><span class="sxs-lookup"><span data-stu-id="c7d1b-127">where the directory size is `N * 8`.</span></span>  
  
 <span data-ttu-id="c7d1b-128">Formát pro každou položku informace o vytváření instancí v haldě je:</span><span class="sxs-lookup"><span data-stu-id="c7d1b-128">The format for each instantiation information item on the heap is:</span></span>  
  
-   <span data-ttu-id="c7d1b-129">Délka této položky informace o vytváření instancí v bajtech v komprimované ECMA metadata formátu.</span><span class="sxs-lookup"><span data-stu-id="c7d1b-129">The length of this instantiation information item in bytes in compressed ECMA metadata format.</span></span> <span data-ttu-id="c7d1b-130">Hodnota vyloučí tyto informace délka.</span><span class="sxs-lookup"><span data-stu-id="c7d1b-130">The value excludes this length information.</span></span>  
  
-   <span data-ttu-id="c7d1b-131">Počet typů obecné konkretizaci nebo *T*, ve formátu metadat komprimované ECMA.</span><span class="sxs-lookup"><span data-stu-id="c7d1b-131">The number of generic instantiation types, or *T*, in compressed ECMA metadata format.</span></span>  
  
-   <span data-ttu-id="c7d1b-132">*T* typy, každý určený ve formátu podpis ECMA typu.</span><span class="sxs-lookup"><span data-stu-id="c7d1b-132">*T* types, each represented in ECMA type signature format.</span></span>  
  
 <span data-ttu-id="c7d1b-133">Zahrnutí délka pro každý prvek haldy umožňuje jednoduché řazení sekci adresáře bez ovlivnění haldě.</span><span class="sxs-lookup"><span data-stu-id="c7d1b-133">The inclusion of the length for each heap element enables simple sorting of the directory section without affecting the heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7d1b-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7d1b-134">Requirements</span></span>  
 <span data-ttu-id="c7d1b-135">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7d1b-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7d1b-136">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7d1b-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7d1b-137">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7d1b-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7d1b-138">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7d1b-138">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d1b-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7d1b-139">See Also</span></span>  
 [<span data-ttu-id="c7d1b-140">ICorDebugSymbolProvider2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c7d1b-140">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [<span data-ttu-id="c7d1b-141">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c7d1b-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
