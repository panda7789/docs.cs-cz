---
title: ICorDebugSymbolProvider – rozhraní
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc33018f68f9634a29e2f5c52123a0215b446de7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61953235"
---
# <a name="icordebugsymbolprovider-interface"></a><span data-ttu-id="cbf20-102">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cbf20-102">ICorDebugSymbolProvider Interface</span></span>
<span data-ttu-id="cbf20-103">Poskytuje metody, které slouží k načtení informací symbolů ladění.</span><span class="sxs-lookup"><span data-stu-id="cbf20-103">Provides methods that can be used to retrieve debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cbf20-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cbf20-104">Methods</span></span>  
  
|<span data-ttu-id="cbf20-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cbf20-105">Method</span></span>|<span data-ttu-id="cbf20-106">Popis</span><span class="sxs-lookup"><span data-stu-id="cbf20-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cbf20-107">GetAssemblyImageBytes – metoda</span><span class="sxs-lookup"><span data-stu-id="cbf20-107">GetAssemblyImageBytes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagebytes-method.md)|<span data-ttu-id="cbf20-108">Přečte data ze sloučeného sestavení sloučeného sestavení podle relativní virtuální adresu (RVA).</span><span class="sxs-lookup"><span data-stu-id="cbf20-108">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>|  
|[<span data-ttu-id="cbf20-109">GetAssemblyImageMetadata – metoda</span><span class="sxs-lookup"><span data-stu-id="cbf20-109">GetAssemblyImageMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagemetadata-method.md)|<span data-ttu-id="cbf20-110">Vrátí metadata ze sloučeného sestavení.</span><span class="sxs-lookup"><span data-stu-id="cbf20-110">Returns the metadata from a merged assembly.</span></span>|  
|[<span data-ttu-id="cbf20-111">GetCodeRange – metoda</span><span class="sxs-lookup"><span data-stu-id="cbf20-111">GetCodeRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getcoderange-method.md)|<span data-ttu-id="cbf20-112">Získá počáteční adresa metody a velikost relativní virtuální adresu (RVA) v metodě.</span><span class="sxs-lookup"><span data-stu-id="cbf20-112">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>|  
|[<span data-ttu-id="cbf20-113">GetInstanceFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="cbf20-113">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)|<span data-ttu-id="cbf20-114">Získá instanci symboly pole, které odpovídají token typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="cbf20-114">Gets the instance field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="cbf20-115">GetMergedAssemblyRecords – metoda</span><span class="sxs-lookup"><span data-stu-id="cbf20-115">GetMergedAssemblyRecords Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmergedassemblyrecords-method.md)|<span data-ttu-id="cbf20-116">Získá záznamy symbolů pro sloučený sestavení.</span><span class="sxs-lookup"><span data-stu-id="cbf20-116">Gets the symbol records for all the merged assemblies.</span></span>|  
|[<span data-ttu-id="cbf20-117">GetMethodLocalSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="cbf20-117">GetMethodLocalSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)|<span data-ttu-id="cbf20-118">Získá místní symboly metody uvedené relativní virtuální adresu (RVA) této metody.</span><span class="sxs-lookup"><span data-stu-id="cbf20-118">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="cbf20-119">GetMethodParameterSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="cbf20-119">GetMethodParameterSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)|<span data-ttu-id="cbf20-120">Získá symboly parametr metody uvedené relativní virtuální adresu (RVA) této metody.</span><span class="sxs-lookup"><span data-stu-id="cbf20-120">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="cbf20-121">GetMethodProps – metoda</span><span class="sxs-lookup"><span data-stu-id="cbf20-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)|<span data-ttu-id="cbf20-122">Vrátí informace o vlastnostech metody, jako je například token metadat a informace o obecných parametrů, metody-li zadána relativní virtuální adresu (RVA) v této metodě.</span><span class="sxs-lookup"><span data-stu-id="cbf20-122">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>|  
|[<span data-ttu-id="cbf20-123">GetObjectSize – metoda</span><span class="sxs-lookup"><span data-stu-id="cbf20-123">GetObjectSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getobjectsize-method.md)|<span data-ttu-id="cbf20-124">Vrátí velikost objektu pro objekt závislosti na jeho token typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="cbf20-124">Returns the object size for an object based on its typespec signature.</span></span>|  
|[<span data-ttu-id="cbf20-125">GetStaticFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="cbf20-125">GetStaticFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)|<span data-ttu-id="cbf20-126">Získá statické pole symboly, které odpovídají token typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="cbf20-126">Gets the static field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="cbf20-127">GetTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="cbf20-127">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)|<span data-ttu-id="cbf20-128">Vrátí informace o typu vlastnosti, jako je počet podpis jeho obecné parametry-li zadána relativní virtuální adresu (RVA) v tabulku vtable.</span><span class="sxs-lookup"><span data-stu-id="cbf20-128">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbf20-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cbf20-129">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cbf20-130">Toto rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cbf20-130">This interface is available with .NET Native only.</span></span> <span data-ttu-id="cbf20-131">Pokud se rozhodnete implementovat toto rozhraní ICorDebug scénářích mimo .NET Native, modul common language runtime bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cbf20-131">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbf20-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cbf20-132">Requirements</span></span>  
 <span data-ttu-id="cbf20-133">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbf20-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbf20-134">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cbf20-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cbf20-135">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbf20-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbf20-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbf20-136">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbf20-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cbf20-137">See also</span></span>

- [<span data-ttu-id="cbf20-138">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="cbf20-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="cbf20-139">Ladění</span><span class="sxs-lookup"><span data-stu-id="cbf20-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
