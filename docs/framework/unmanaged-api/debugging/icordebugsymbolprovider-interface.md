---
title: "ICorDebugSymbolProvider rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 96f5d897b1f426fd85fd274d5e56e8726b8cb892
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovider-interface"></a><span data-ttu-id="b9fec-102">ICorDebugSymbolProvider rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9fec-102">ICorDebugSymbolProvider Interface</span></span>
<span data-ttu-id="b9fec-103">Poskytuje metody, které lze použít k načtení informací o symbolu ladění.</span><span class="sxs-lookup"><span data-stu-id="b9fec-103">Provides methods that can be used to retrieve debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b9fec-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b9fec-104">Methods</span></span>  
  
|<span data-ttu-id="b9fec-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b9fec-105">Method</span></span>|<span data-ttu-id="b9fec-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b9fec-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b9fec-107">GetAssemblyImageBytes – metoda</span><span class="sxs-lookup"><span data-stu-id="b9fec-107">GetAssemblyImageBytes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagebytes-method.md)|<span data-ttu-id="b9fec-108">Čte data z sloučené sestavení zadaný relativní virtuální adresy (RVA) v sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="b9fec-108">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>|  
|[<span data-ttu-id="b9fec-109">GetAssemblyImageMetadata – metoda</span><span class="sxs-lookup"><span data-stu-id="b9fec-109">GetAssemblyImageMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagemetadata-method.md)|<span data-ttu-id="b9fec-110">Vrátí metadata z sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="b9fec-110">Returns the metadata from a merged assembly.</span></span>|  
|[<span data-ttu-id="b9fec-111">GetCodeRange – metoda</span><span class="sxs-lookup"><span data-stu-id="b9fec-111">GetCodeRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getcoderange-method.md)|<span data-ttu-id="b9fec-112">Získá metoda počáteční adresy a velikost relativní virtuální adresy (RVA) v metodu.</span><span class="sxs-lookup"><span data-stu-id="b9fec-112">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>|  
|[<span data-ttu-id="b9fec-113">GetInstanceFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="b9fec-113">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)|<span data-ttu-id="b9fec-114">Získá instanci symbolů pole, které odpovídají typ typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="b9fec-114">Gets the instance field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="b9fec-115">GetMergedAssemblyRecords – metoda</span><span class="sxs-lookup"><span data-stu-id="b9fec-115">GetMergedAssemblyRecords Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmergedassemblyrecords-method.md)|<span data-ttu-id="b9fec-116">Získá záznamy symbol pro sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="b9fec-116">Gets the symbol records for all the merged assemblies.</span></span>|  
|[<span data-ttu-id="b9fec-117">GetMethodLocalSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="b9fec-117">GetMethodLocalSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)|<span data-ttu-id="b9fec-118">Získá symboly místní metoda zadaný relativní virtuální adresa (RVA) této metody.</span><span class="sxs-lookup"><span data-stu-id="b9fec-118">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="b9fec-119">GetMethodParameterSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="b9fec-119">GetMethodParameterSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)|<span data-ttu-id="b9fec-120">Získá symboly metoda parametr zadaný relativní virtuální adresa (RVA) této metody.</span><span class="sxs-lookup"><span data-stu-id="b9fec-120">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="b9fec-121">Getmethodprops – metoda</span><span class="sxs-lookup"><span data-stu-id="b9fec-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)|<span data-ttu-id="b9fec-122">Zadaná relativní virtuální adresy (RVA) v dané metody vrací informace o vlastnosti metoda, například metadata token a informace o jeho obecné parametry metody.</span><span class="sxs-lookup"><span data-stu-id="b9fec-122">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>|  
|[<span data-ttu-id="b9fec-123">Getobjectsize – metoda</span><span class="sxs-lookup"><span data-stu-id="b9fec-123">GetObjectSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getobjectsize-method.md)|<span data-ttu-id="b9fec-124">Vrátí velikost objektu pro objekt podle jeho typ typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="b9fec-124">Returns the object size for an object based on its typespec signature.</span></span>|  
|[<span data-ttu-id="b9fec-125">GetStaticFieldSymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="b9fec-125">GetStaticFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)|<span data-ttu-id="b9fec-126">Získá symboly statické pole, které odpovídají typ typespec podpis.</span><span class="sxs-lookup"><span data-stu-id="b9fec-126">Gets the static field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="b9fec-127">GetTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="b9fec-127">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)|<span data-ttu-id="b9fec-128">Zadaný relativní virtuální adresy (RVA) v tabulce vtable vrací informace o vlastnosti typ, například počet podpis jeho obecné parametry.</span><span class="sxs-lookup"><span data-stu-id="b9fec-128">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9fec-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b9fec-129">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9fec-130">Toto rozhraní je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="b9fec-130">This interface is available with .NET Native only.</span></span> <span data-ttu-id="b9fec-131">Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b9fec-131">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9fec-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b9fec-132">Requirements</span></span>  
 <span data-ttu-id="b9fec-133">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9fec-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9fec-134">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9fec-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9fec-135">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9fec-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9fec-136">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9fec-136">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9fec-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9fec-137">See Also</span></span>  
 [<span data-ttu-id="b9fec-138">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9fec-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b9fec-139">Ladění</span><span class="sxs-lookup"><span data-stu-id="b9fec-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
