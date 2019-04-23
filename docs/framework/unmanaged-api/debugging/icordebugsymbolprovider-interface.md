---
title: ICorDebugSymbolProvider – rozhraní
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc33018f68f9634a29e2f5c52123a0215b446de7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59228962"
---
# <a name="icordebugsymbolprovider-interface"></a><span data-ttu-id="81d0b-102">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="81d0b-102">ICorDebugSymbolProvider Interface</span></span>
<span data-ttu-id="81d0b-103">Poskytuje metody, které slouží k načtení informací symbolů ladění.</span><span class="sxs-lookup"><span data-stu-id="81d0b-103">Provides methods that can be used to retrieve debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="81d0b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="81d0b-104">Methods</span></span>  
  
|<span data-ttu-id="81d0b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="81d0b-105">Method</span></span>|<span data-ttu-id="81d0b-106">Popis</span><span class="sxs-lookup"><span data-stu-id="81d0b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="81d0b-107">GetAssemblyImageBytes – metoda</span><span class="sxs-lookup"><span data-stu-id="81d0b-107">GetAssemblyImageBytes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagebytes-method.md)|<span data-ttu-id="81d0b-108">Přečte data ze sloučeného sestavení sloučeného sestavení podle relativní virtuální adresu (RVA).</span><span class="sxs-lookup"><span data-stu-id="81d0b-108">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>|  
|[<span data-ttu-id="81d0b-109">GetAssemblyImageMetadata – metoda</span><span class="sxs-lookup"><span data-stu-id="81d0b-109">GetAssemblyImageMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagemetadata-method.md)|<span data-ttu-id="81d0b-110">Vrátí metadata ze sloučeného sestavení.</span><span class="sxs-lookup"><span data-stu-id="81d0b-110">Returns the metadata from a merged assembly.</span></span>|  
|[<span data-ttu-id="81d0b-111">GetCodeRange – metoda</span><span class="sxs-lookup"><span data-stu-id="81d0b-111">GetCodeRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getcoderange-method.md)|<span data-ttu-id="81d0b-112">Získá počáteční adresa metody a velikost relativní virtuální adresu (RVA) v metodě.</span><span class="sxs-lookup"><span data-stu-id="81d0b-112">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>|  
|[<span data-ttu-id="81d0b-113">GetInstanceFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="81d0b-113">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)|<span data-ttu-id="81d0b-114">Získá instanci symboly pole, které odpovídají token typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="81d0b-114">Gets the instance field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="81d0b-115">GetMergedAssemblyRecords – metoda</span><span class="sxs-lookup"><span data-stu-id="81d0b-115">GetMergedAssemblyRecords Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmergedassemblyrecords-method.md)|<span data-ttu-id="81d0b-116">Získá záznamy symbolů pro sloučený sestavení.</span><span class="sxs-lookup"><span data-stu-id="81d0b-116">Gets the symbol records for all the merged assemblies.</span></span>|  
|[<span data-ttu-id="81d0b-117">GetMethodLocalSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="81d0b-117">GetMethodLocalSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)|<span data-ttu-id="81d0b-118">Získá místní symboly metody uvedené relativní virtuální adresu (RVA) této metody.</span><span class="sxs-lookup"><span data-stu-id="81d0b-118">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="81d0b-119">GetMethodParameterSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="81d0b-119">GetMethodParameterSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)|<span data-ttu-id="81d0b-120">Získá symboly parametr metody uvedené relativní virtuální adresu (RVA) této metody.</span><span class="sxs-lookup"><span data-stu-id="81d0b-120">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="81d0b-121">GetMethodProps – metoda</span><span class="sxs-lookup"><span data-stu-id="81d0b-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)|<span data-ttu-id="81d0b-122">Vrátí informace o vlastnostech metody, jako je například token metadat a informace o obecných parametrů, metody-li zadána relativní virtuální adresu (RVA) v této metodě.</span><span class="sxs-lookup"><span data-stu-id="81d0b-122">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>|  
|[<span data-ttu-id="81d0b-123">GetObjectSize – metoda</span><span class="sxs-lookup"><span data-stu-id="81d0b-123">GetObjectSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getobjectsize-method.md)|<span data-ttu-id="81d0b-124">Vrátí velikost objektu pro objekt závislosti na jeho token typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="81d0b-124">Returns the object size for an object based on its typespec signature.</span></span>|  
|[<span data-ttu-id="81d0b-125">GetStaticFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="81d0b-125">GetStaticFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)|<span data-ttu-id="81d0b-126">Získá statické pole symboly, které odpovídají token typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="81d0b-126">Gets the static field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="81d0b-127">GetTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="81d0b-127">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)|<span data-ttu-id="81d0b-128">Vrátí informace o typu vlastnosti, jako je počet podpis jeho obecné parametry-li zadána relativní virtuální adresu (RVA) v tabulku vtable.</span><span class="sxs-lookup"><span data-stu-id="81d0b-128">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81d0b-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81d0b-129">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81d0b-130">Toto rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="81d0b-130">This interface is available with .NET Native only.</span></span> <span data-ttu-id="81d0b-131">Pokud se rozhodnete implementovat toto rozhraní ICorDebug scénářích mimo .NET Native, modul common language runtime bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="81d0b-131">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81d0b-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="81d0b-132">Requirements</span></span>  
 <span data-ttu-id="81d0b-133">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81d0b-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81d0b-134">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81d0b-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81d0b-135">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81d0b-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81d0b-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81d0b-136">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81d0b-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81d0b-137">See also</span></span>

- [<span data-ttu-id="81d0b-138">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="81d0b-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="81d0b-139">Ladění</span><span class="sxs-lookup"><span data-stu-id="81d0b-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
