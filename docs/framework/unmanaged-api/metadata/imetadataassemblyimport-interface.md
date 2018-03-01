---
title: "IMetaDataAssemblyImport – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataAssemblyImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport
helpviewer_keywords:
- IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 992b588d16bc221f6b72044da40d09fbb6894511
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="09b7f-102">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="09b7f-102">IMetaDataAssemblyImport Interface</span></span>
<span data-ttu-id="09b7f-103">Poskytuje metody pro přístup a kontrolu obsah manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="09b7f-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="09b7f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="09b7f-104">Methods</span></span>  
  
|<span data-ttu-id="09b7f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="09b7f-105">Method</span></span>|<span data-ttu-id="09b7f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="09b7f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="09b7f-107">CloseEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="09b7f-107">CloseEnum Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="09b7f-108">Uvolní popisovač zadaný enumerátor.</span><span class="sxs-lookup"><span data-stu-id="09b7f-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="09b7f-109">EnumAssemblyRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="09b7f-109">EnumAssemblyRefs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="09b7f-110">Získá ukazatele rozhraní na enumerátor, který obsahuje `mdAssemblyRef` tokeny sestavení odkazuje sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="09b7f-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="09b7f-111">EnumExportedTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="09b7f-111">EnumExportedTypes Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="09b7f-112">Získá ukazatele rozhraní na enumerátor, který obsahuje `mdExportedType` tokeny typy modelu COM, odkazuje na sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="09b7f-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="09b7f-113">EnumFiles – metoda</span><span class="sxs-lookup"><span data-stu-id="09b7f-113">EnumFiles Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="09b7f-114">Získá ukazatele rozhraní na enumerátor, který obsahuje `mdFile` tokeny souborů odkazuje sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="09b7f-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="09b7f-115">EnumManifestResources – metoda</span><span class="sxs-lookup"><span data-stu-id="09b7f-115">EnumManifestResources Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="09b7f-116">Získá ukazatele rozhraní na enumerátor, který obsahuje `mdManifestResource` tokeny prostředků odkazuje sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="09b7f-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="09b7f-117">FindAssembliesByName – metoda</span><span class="sxs-lookup"><span data-stu-id="09b7f-117">FindAssembliesByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="09b7f-118">Získá pole `mdAssemblyRef` tokeny pro sestavení se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="09b7f-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="09b7f-119">FindExportedTypeByName – metoda</span><span class="sxs-lookup"><span data-stu-id="09b7f-119">FindExportedTypeByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="09b7f-120">Získá `mdExportedType` tokenu pro typ COM se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="09b7f-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="09b7f-121">FindManifestResourceByName – metoda</span><span class="sxs-lookup"><span data-stu-id="09b7f-121">FindManifestResourceByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="09b7f-122">Získá `mdManifestResource` tokenu pro prostředek se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="09b7f-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="09b7f-123">GetAssemblyFromScope – metoda</span><span class="sxs-lookup"><span data-stu-id="09b7f-123">GetAssemblyFromScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="09b7f-124">Získá token pro sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="09b7f-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="09b7f-125">GetAssemblyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="09b7f-125">GetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="09b7f-126">Získá nastavení vlastností zadaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="09b7f-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="09b7f-127">GetAssemblyRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="09b7f-127">GetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="09b7f-128">Získá nastavení vlastností zadaného `mdAssemblyRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="09b7f-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="09b7f-129">GetExportedTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="09b7f-129">GetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="09b7f-130">Získá nastavení vlastností zadaného typu modelu COM.</span><span class="sxs-lookup"><span data-stu-id="09b7f-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="09b7f-131">GetFileProps – metoda</span><span class="sxs-lookup"><span data-stu-id="09b7f-131">GetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="09b7f-132">Získá nastavení vlastností zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="09b7f-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="09b7f-133">GetManifestResourceProps – metoda</span><span class="sxs-lookup"><span data-stu-id="09b7f-133">GetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="09b7f-134">Získá nastavení vlastností zadaného prostředku manifestu.</span><span class="sxs-lookup"><span data-stu-id="09b7f-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="09b7f-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="09b7f-135">Requirements</span></span>  
 <span data-ttu-id="09b7f-136">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09b7f-136">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09b7f-137">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="09b7f-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="09b7f-138">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="09b7f-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="09b7f-139">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09b7f-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09b7f-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="09b7f-140">See Also</span></span>  
 [<span data-ttu-id="09b7f-141">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="09b7f-141">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="09b7f-142">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="09b7f-142">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
