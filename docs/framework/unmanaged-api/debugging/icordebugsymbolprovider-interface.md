---
title: ICorDebugSymbolProvider – rozhraní
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
ms.openlocfilehash: 25faad4f4bc67b57c339bc63d1a18ab4d275cd71
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379345"
---
# <a name="icordebugsymbolprovider-interface"></a><span data-ttu-id="be0c5-102">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="be0c5-102">ICorDebugSymbolProvider Interface</span></span>
<span data-ttu-id="be0c5-103">Poskytuje metody, které lze použít k načtení informací o symbolech ladění.</span><span class="sxs-lookup"><span data-stu-id="be0c5-103">Provides methods that can be used to retrieve debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="be0c5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="be0c5-104">Methods</span></span>  
  
|<span data-ttu-id="be0c5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="be0c5-105">Method</span></span>|<span data-ttu-id="be0c5-106">Popis</span><span class="sxs-lookup"><span data-stu-id="be0c5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="be0c5-107">GetAssemblyImageBytes – metoda</span><span class="sxs-lookup"><span data-stu-id="be0c5-107">GetAssemblyImageBytes Method</span></span>](icordebugsymbolprovider-getassemblyimagebytes-method.md)|<span data-ttu-id="be0c5-108">Načte data ze sloučeného sestavení s ohledem na relativní virtuální adresu (RVA) ve sloučeném sestavení.</span><span class="sxs-lookup"><span data-stu-id="be0c5-108">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>|  
|[<span data-ttu-id="be0c5-109">GetAssemblyImageMetadata – metoda</span><span class="sxs-lookup"><span data-stu-id="be0c5-109">GetAssemblyImageMetadata Method</span></span>](icordebugsymbolprovider-getassemblyimagemetadata-method.md)|<span data-ttu-id="be0c5-110">Vrátí metadata ze sloučeného sestavení.</span><span class="sxs-lookup"><span data-stu-id="be0c5-110">Returns the metadata from a merged assembly.</span></span>|  
|[<span data-ttu-id="be0c5-111">GetCodeRange – metoda</span><span class="sxs-lookup"><span data-stu-id="be0c5-111">GetCodeRange Method</span></span>](icordebugsymbolprovider-getcoderange-method.md)|<span data-ttu-id="be0c5-112">Získá počáteční adresu a velikost metody dané relativní virtuální adresy (RVA) v metodě.</span><span class="sxs-lookup"><span data-stu-id="be0c5-112">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>|  
|[<span data-ttu-id="be0c5-113">GetInstanceFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="be0c5-113">GetInstanceFieldSymbols Method</span></span>](icordebugsymbolprovider-getinstancefieldsymbols-method.md)|<span data-ttu-id="be0c5-114">Načte symboly pole instance, které odpovídají token TypeSpec podpisu.</span><span class="sxs-lookup"><span data-stu-id="be0c5-114">Gets the instance field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="be0c5-115">GetMergedAssemblyRecords – metoda</span><span class="sxs-lookup"><span data-stu-id="be0c5-115">GetMergedAssemblyRecords Method</span></span>](icordebugsymbolprovider-getmergedassemblyrecords-method.md)|<span data-ttu-id="be0c5-116">Získá záznamy symbolů pro všechna Sloučená sestavení.</span><span class="sxs-lookup"><span data-stu-id="be0c5-116">Gets the symbol records for all the merged assemblies.</span></span>|  
|[<span data-ttu-id="be0c5-117">GetMethodLocalSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="be0c5-117">GetMethodLocalSymbols Method</span></span>](icordebugsymbolprovider-getmethodlocalsymbols-method.md)|<span data-ttu-id="be0c5-118">Načte místní symboly metody s relativní virtuální adresou (RVA) dané metody.</span><span class="sxs-lookup"><span data-stu-id="be0c5-118">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="be0c5-119">GetMethodParameterSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="be0c5-119">GetMethodParameterSymbols Method</span></span>](icordebugsymbolprovider-getmethodparametersymbols-method.md)|<span data-ttu-id="be0c5-120">Načte symboly parametrů metody vzhledem k relativní virtuální adrese (RVA) dané metody.</span><span class="sxs-lookup"><span data-stu-id="be0c5-120">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="be0c5-121">GetMethodProps – metoda</span><span class="sxs-lookup"><span data-stu-id="be0c5-121">GetMethodProps Method</span></span>](icordebugsymbolprovider-getmethodprops-method.md)|<span data-ttu-id="be0c5-122">Vrátí informace o vlastnostech metody, jako je token metadat metody a informace o jeho obecných parametrech, s ohledem na relativní virtuální adresu (RVA) v této metodě.</span><span class="sxs-lookup"><span data-stu-id="be0c5-122">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>|  
|[<span data-ttu-id="be0c5-123">GetObjectSize – metoda</span><span class="sxs-lookup"><span data-stu-id="be0c5-123">GetObjectSize Method</span></span>](icordebugsymbolprovider-getobjectsize-method.md)|<span data-ttu-id="be0c5-124">Vrátí velikost objektu objektu na základě jeho signatury token TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="be0c5-124">Returns the object size for an object based on its typespec signature.</span></span>|  
|[<span data-ttu-id="be0c5-125">GetStaticFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="be0c5-125">GetStaticFieldSymbols Method</span></span>](icordebugsymbolprovider-getstaticfieldsymbols-method.md)|<span data-ttu-id="be0c5-126">Získá symboly statického pole, které odpovídají token TypeSpec podpisu.</span><span class="sxs-lookup"><span data-stu-id="be0c5-126">Gets the static field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="be0c5-127">GetTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="be0c5-127">GetTypeProps Method</span></span>](icordebugsymbolprovider-gettypeprops-method.md)|<span data-ttu-id="be0c5-128">Vrátí informace o vlastnostech typu, jako je například počet podpisů svých obecných parametrů, s ohledem na relativní virtuální adresu (RVA) v tabulce vtable.</span><span class="sxs-lookup"><span data-stu-id="be0c5-128">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be0c5-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="be0c5-129">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be0c5-130">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="be0c5-130">This interface is available with .NET Native only.</span></span> <span data-ttu-id="be0c5-131">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="be0c5-131">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be0c5-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="be0c5-132">Requirements</span></span>  
 <span data-ttu-id="be0c5-133">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be0c5-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be0c5-134">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="be0c5-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be0c5-135">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="be0c5-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be0c5-136">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be0c5-136">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be0c5-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="be0c5-137">See also</span></span>

- [<span data-ttu-id="be0c5-138">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="be0c5-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="be0c5-139">Ladění</span><span class="sxs-lookup"><span data-stu-id="be0c5-139">Debugging</span></span>](index.md)
