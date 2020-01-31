---
title: ICorDebugSymbolProvider – rozhraní
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
ms.openlocfilehash: 6f7a8a2b12c047b956a3b6e85fe8365e0360b3f2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791533"
---
# <a name="icordebugsymbolprovider-interface"></a><span data-ttu-id="b6924-102">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6924-102">ICorDebugSymbolProvider Interface</span></span>
<span data-ttu-id="b6924-103">Poskytuje metody, které lze použít k načtení informací o symbolech ladění.</span><span class="sxs-lookup"><span data-stu-id="b6924-103">Provides methods that can be used to retrieve debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b6924-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b6924-104">Methods</span></span>  
  
|<span data-ttu-id="b6924-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b6924-105">Method</span></span>|<span data-ttu-id="b6924-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b6924-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b6924-107">GetAssemblyImageBytes – metoda</span><span class="sxs-lookup"><span data-stu-id="b6924-107">GetAssemblyImageBytes Method</span></span>](icordebugsymbolprovider-getassemblyimagebytes-method.md)|<span data-ttu-id="b6924-108">Načte data ze sloučeného sestavení s ohledem na relativní virtuální adresu (RVA) ve sloučeném sestavení.</span><span class="sxs-lookup"><span data-stu-id="b6924-108">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>|  
|[<span data-ttu-id="b6924-109">GetAssemblyImageMetadata – metoda</span><span class="sxs-lookup"><span data-stu-id="b6924-109">GetAssemblyImageMetadata Method</span></span>](icordebugsymbolprovider-getassemblyimagemetadata-method.md)|<span data-ttu-id="b6924-110">Vrátí metadata ze sloučeného sestavení.</span><span class="sxs-lookup"><span data-stu-id="b6924-110">Returns the metadata from a merged assembly.</span></span>|  
|[<span data-ttu-id="b6924-111">GetCodeRange – metoda</span><span class="sxs-lookup"><span data-stu-id="b6924-111">GetCodeRange Method</span></span>](icordebugsymbolprovider-getcoderange-method.md)|<span data-ttu-id="b6924-112">Získá počáteční adresu a velikost metody dané relativní virtuální adresy (RVA) v metodě.</span><span class="sxs-lookup"><span data-stu-id="b6924-112">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>|  
|[<span data-ttu-id="b6924-113">GetInstanceFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="b6924-113">GetInstanceFieldSymbols Method</span></span>](icordebugsymbolprovider-getinstancefieldsymbols-method.md)|<span data-ttu-id="b6924-114">Načte symboly pole instance, které odpovídají token TypeSpec podpisu.</span><span class="sxs-lookup"><span data-stu-id="b6924-114">Gets the instance field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="b6924-115">GetMergedAssemblyRecords – metoda</span><span class="sxs-lookup"><span data-stu-id="b6924-115">GetMergedAssemblyRecords Method</span></span>](icordebugsymbolprovider-getmergedassemblyrecords-method.md)|<span data-ttu-id="b6924-116">Získá záznamy symbolů pro všechna Sloučená sestavení.</span><span class="sxs-lookup"><span data-stu-id="b6924-116">Gets the symbol records for all the merged assemblies.</span></span>|  
|[<span data-ttu-id="b6924-117">GetMethodLocalSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="b6924-117">GetMethodLocalSymbols Method</span></span>](icordebugsymbolprovider-getmethodlocalsymbols-method.md)|<span data-ttu-id="b6924-118">Načte místní symboly metody s relativní virtuální adresou (RVA) dané metody.</span><span class="sxs-lookup"><span data-stu-id="b6924-118">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="b6924-119">GetMethodParameterSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="b6924-119">GetMethodParameterSymbols Method</span></span>](icordebugsymbolprovider-getmethodparametersymbols-method.md)|<span data-ttu-id="b6924-120">Načte symboly parametrů metody vzhledem k relativní virtuální adrese (RVA) dané metody.</span><span class="sxs-lookup"><span data-stu-id="b6924-120">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="b6924-121">GetMethodProps – metoda</span><span class="sxs-lookup"><span data-stu-id="b6924-121">GetMethodProps Method</span></span>](icordebugsymbolprovider-getmethodprops-method.md)|<span data-ttu-id="b6924-122">Vrátí informace o vlastnostech metody, jako je token metadat metody a informace o jeho obecných parametrech, s ohledem na relativní virtuální adresu (RVA) v této metodě.</span><span class="sxs-lookup"><span data-stu-id="b6924-122">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>|  
|[<span data-ttu-id="b6924-123">GetObjectSize – metoda</span><span class="sxs-lookup"><span data-stu-id="b6924-123">GetObjectSize Method</span></span>](icordebugsymbolprovider-getobjectsize-method.md)|<span data-ttu-id="b6924-124">Vrátí velikost objektu objektu na základě jeho signatury token TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="b6924-124">Returns the object size for an object based on its typespec signature.</span></span>|  
|[<span data-ttu-id="b6924-125">GetStaticFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="b6924-125">GetStaticFieldSymbols Method</span></span>](icordebugsymbolprovider-getstaticfieldsymbols-method.md)|<span data-ttu-id="b6924-126">Získá symboly statického pole, které odpovídají token TypeSpec podpisu.</span><span class="sxs-lookup"><span data-stu-id="b6924-126">Gets the static field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="b6924-127">GetTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="b6924-127">GetTypeProps Method</span></span>](icordebugsymbolprovider-gettypeprops-method.md)|<span data-ttu-id="b6924-128">Vrátí informace o vlastnostech typu, jako je například počet podpisů svých obecných parametrů, s ohledem na relativní virtuální adresu (RVA) v tabulce vtable.</span><span class="sxs-lookup"><span data-stu-id="b6924-128">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6924-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b6924-129">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6924-130">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b6924-130">This interface is available with .NET Native only.</span></span> <span data-ttu-id="b6924-131">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="b6924-131">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6924-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b6924-132">Requirements</span></span>  
 <span data-ttu-id="b6924-133">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6924-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6924-134">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b6924-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6924-135">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b6924-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6924-136">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6924-136">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6924-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6924-137">See also</span></span>

- [<span data-ttu-id="b6924-138">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b6924-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b6924-139">Ladění</span><span class="sxs-lookup"><span data-stu-id="b6924-139">Debugging</span></span>](index.md)
