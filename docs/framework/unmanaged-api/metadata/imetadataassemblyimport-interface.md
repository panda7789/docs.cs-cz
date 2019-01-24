---
title: IMetaDataAssemblyImport – rozhraní
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9f213bcb9f87c34d23b53c2016bd841aae7c7194
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540273"
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="c06b6-102">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c06b6-102">IMetaDataAssemblyImport Interface</span></span>
<span data-ttu-id="c06b6-103">Poskytuje metody pro přístup k a zkontrolovat obsah manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="c06b6-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c06b6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c06b6-104">Methods</span></span>  
  
|<span data-ttu-id="c06b6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c06b6-105">Method</span></span>|<span data-ttu-id="c06b6-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c06b6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c06b6-107">CloseEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="c06b6-107">CloseEnum Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="c06b6-108">Uvolní popisovač pro zadaný čítač.</span><span class="sxs-lookup"><span data-stu-id="c06b6-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="c06b6-109">EnumAssemblyRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="c06b6-109">EnumAssemblyRefs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="c06b6-110">Získá enumerátor, který obsahuje ukazatel rozhraní `mdAssemblyRef` tokeny sestavení odkazuje sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="c06b6-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="c06b6-111">EnumExportedTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="c06b6-111">EnumExportedTypes Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="c06b6-112">Získá enumerátor, který obsahuje ukazatel rozhraní `mdExportedType` tokeny typů modelu COM, který odkazuje na sestavení v aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="c06b6-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="c06b6-113">EnumFiles – metoda</span><span class="sxs-lookup"><span data-stu-id="c06b6-113">EnumFiles Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="c06b6-114">Získá enumerátor, který obsahuje ukazatel rozhraní `mdFile` tokeny soubory odkazované sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="c06b6-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="c06b6-115">EnumManifestResources – metoda</span><span class="sxs-lookup"><span data-stu-id="c06b6-115">EnumManifestResources Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="c06b6-116">Získá enumerátor, který obsahuje ukazatel rozhraní `mdManifestResource` tokeny prostředků odkazuje na sestavení v aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="c06b6-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="c06b6-117">FindAssembliesByName – metoda</span><span class="sxs-lookup"><span data-stu-id="c06b6-117">FindAssembliesByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="c06b6-118">Získává pole `mdAssemblyRef` tokeny pro sestavení se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="c06b6-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="c06b6-119">FindExportedTypeByName – metoda</span><span class="sxs-lookup"><span data-stu-id="c06b6-119">FindExportedTypeByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="c06b6-120">Získá `mdExportedType` tokenů pro typ modelu COM se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="c06b6-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="c06b6-121">FindManifestResourceByName – metoda</span><span class="sxs-lookup"><span data-stu-id="c06b6-121">FindManifestResourceByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="c06b6-122">Získá `mdManifestResource` token pro prostředek se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="c06b6-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="c06b6-123">GetAssemblyFromScope – metoda</span><span class="sxs-lookup"><span data-stu-id="c06b6-123">GetAssemblyFromScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="c06b6-124">Získá token pro sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="c06b6-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="c06b6-125">GetAssemblyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="c06b6-125">GetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="c06b6-126">Získá nastavení vlastností zadaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="c06b6-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="c06b6-127">GetAssemblyRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="c06b6-127">GetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="c06b6-128">Získá nastavení vlastností zadaného `mdAssemblyRef` token.</span><span class="sxs-lookup"><span data-stu-id="c06b6-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="c06b6-129">GetExportedTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="c06b6-129">GetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="c06b6-130">Získá nastavení vlastností zadaného typu modelu COM.</span><span class="sxs-lookup"><span data-stu-id="c06b6-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="c06b6-131">GetFileProps – metoda</span><span class="sxs-lookup"><span data-stu-id="c06b6-131">GetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="c06b6-132">Získá nastavení vlastností zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="c06b6-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="c06b6-133">GetManifestResourceProps – metoda</span><span class="sxs-lookup"><span data-stu-id="c06b6-133">GetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="c06b6-134">Získá nastavení vlastnosti zadaného prostředku manifestu.</span><span class="sxs-lookup"><span data-stu-id="c06b6-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c06b6-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c06b6-135">Requirements</span></span>  
 <span data-ttu-id="c06b6-136">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c06b6-136">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c06b6-137">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c06b6-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c06b6-138">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c06b6-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c06b6-139">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c06b6-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c06b6-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c06b6-140">See also</span></span>
- [<span data-ttu-id="c06b6-141">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="c06b6-141">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="c06b6-142">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c06b6-142">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
