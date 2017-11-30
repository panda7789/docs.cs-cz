---
title: "IMetaDataAssemblyImport – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport
helpviewer_keywords: IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ef5b913dc9b1391c63cb123e1f922ca61da6a5bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="3c2d5-102">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c2d5-102">IMetaDataAssemblyImport Interface</span></span>
<span data-ttu-id="3c2d5-103">Poskytuje metody pro přístup a kontrolu obsah manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="3c2d5-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3c2d5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3c2d5-104">Methods</span></span>  
  
|<span data-ttu-id="3c2d5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3c2d5-105">Method</span></span>|<span data-ttu-id="3c2d5-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3c2d5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3c2d5-107">Closeenum – metoda</span><span class="sxs-lookup"><span data-stu-id="3c2d5-107">CloseEnum Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="3c2d5-108">Uvolní popisovač zadaný enumerátor.</span><span class="sxs-lookup"><span data-stu-id="3c2d5-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="3c2d5-109">Enumassemblyrefs – metoda</span><span class="sxs-lookup"><span data-stu-id="3c2d5-109">EnumAssemblyRefs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="3c2d5-110">Získá ukazatele rozhraní na enumerátor, který obsahuje `mdAssemblyRef` tokeny sestavení odkazuje sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="3c2d5-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="3c2d5-111">Enumexportedtypes – metoda</span><span class="sxs-lookup"><span data-stu-id="3c2d5-111">EnumExportedTypes Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="3c2d5-112">Získá ukazatele rozhraní na enumerátor, který obsahuje `mdExportedType` tokeny typy modelu COM, odkazuje na sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="3c2d5-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="3c2d5-113">Enumfiles – metoda</span><span class="sxs-lookup"><span data-stu-id="3c2d5-113">EnumFiles Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="3c2d5-114">Získá ukazatele rozhraní na enumerátor, který obsahuje `mdFile` tokeny souborů odkazuje sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="3c2d5-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="3c2d5-115">Enummanifestresources – metoda</span><span class="sxs-lookup"><span data-stu-id="3c2d5-115">EnumManifestResources Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="3c2d5-116">Získá ukazatele rozhraní na enumerátor, který obsahuje `mdManifestResource` tokeny prostředků odkazuje sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="3c2d5-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="3c2d5-117">Findassembliesbyname – metoda</span><span class="sxs-lookup"><span data-stu-id="3c2d5-117">FindAssembliesByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="3c2d5-118">Získá pole `mdAssemblyRef` tokeny pro sestavení se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="3c2d5-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="3c2d5-119">Findexportedtypebyname – metoda</span><span class="sxs-lookup"><span data-stu-id="3c2d5-119">FindExportedTypeByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="3c2d5-120">Získá `mdExportedType` tokenu pro typ COM se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="3c2d5-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="3c2d5-121">Findmanifestresourcebyname – metoda</span><span class="sxs-lookup"><span data-stu-id="3c2d5-121">FindManifestResourceByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="3c2d5-122">Získá `mdManifestResource` tokenu pro prostředek se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="3c2d5-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="3c2d5-123">Getassemblyfromscope – metoda</span><span class="sxs-lookup"><span data-stu-id="3c2d5-123">GetAssemblyFromScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="3c2d5-124">Získá token pro sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="3c2d5-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="3c2d5-125">Getassemblyprops – metoda</span><span class="sxs-lookup"><span data-stu-id="3c2d5-125">GetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="3c2d5-126">Získá nastavení vlastností zadaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="3c2d5-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="3c2d5-127">Getassemblyrefprops – metoda</span><span class="sxs-lookup"><span data-stu-id="3c2d5-127">GetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="3c2d5-128">Získá nastavení vlastností zadaného `mdAssemblyRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="3c2d5-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="3c2d5-129">Getexportedtypeprops – metoda</span><span class="sxs-lookup"><span data-stu-id="3c2d5-129">GetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="3c2d5-130">Získá nastavení vlastností zadaného typu modelu COM.</span><span class="sxs-lookup"><span data-stu-id="3c2d5-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="3c2d5-131">Getfileprops – metoda</span><span class="sxs-lookup"><span data-stu-id="3c2d5-131">GetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="3c2d5-132">Získá nastavení vlastností zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="3c2d5-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="3c2d5-133">Getmanifestresourceprops – metoda</span><span class="sxs-lookup"><span data-stu-id="3c2d5-133">GetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="3c2d5-134">Získá nastavení vlastností zadaného prostředku manifestu.</span><span class="sxs-lookup"><span data-stu-id="3c2d5-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3c2d5-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3c2d5-135">Requirements</span></span>  
 <span data-ttu-id="3c2d5-136">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c2d5-136">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c2d5-137">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3c2d5-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3c2d5-138">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3c2d5-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3c2d5-139">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c2d5-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c2d5-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c2d5-140">See Also</span></span>  
 [<span data-ttu-id="3c2d5-141">Rozhraní metadat</span><span class="sxs-lookup"><span data-stu-id="3c2d5-141">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="3c2d5-142">Imetadataassemblyemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c2d5-142">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
