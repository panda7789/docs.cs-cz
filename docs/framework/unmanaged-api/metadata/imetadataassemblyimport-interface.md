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
ms.openlocfilehash: 289e26868ff2eb9e1d97cf084e9a888815062ea4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436303"
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="0ac36-102">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ac36-102">IMetaDataAssemblyImport Interface</span></span>
<span data-ttu-id="0ac36-103">Poskytuje metody pro přístup k obsahu manifestu sestavení a jeho prohlížení.</span><span class="sxs-lookup"><span data-stu-id="0ac36-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0ac36-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0ac36-104">Methods</span></span>  
  
|<span data-ttu-id="0ac36-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0ac36-105">Method</span></span>|<span data-ttu-id="0ac36-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0ac36-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0ac36-107">CloseEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="0ac36-107">CloseEnum Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="0ac36-108">Uvolní popisovač pro zadaný enumerátor.</span><span class="sxs-lookup"><span data-stu-id="0ac36-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="0ac36-109">EnumAssemblyRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="0ac36-109">EnumAssemblyRefs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="0ac36-110">Získá ukazatel rozhraní na enumerátor, který obsahuje `mdAssemblyRef` tokeny sestavení, na které odkazuje sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="0ac36-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="0ac36-111">EnumExportedTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="0ac36-111">EnumExportedTypes Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="0ac36-112">Získá ukazatel rozhraní na enumerátor, který obsahuje `mdExportedType` tokeny typů COM, na které se odkazuje sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="0ac36-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="0ac36-113">EnumFiles – metoda</span><span class="sxs-lookup"><span data-stu-id="0ac36-113">EnumFiles Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="0ac36-114">Získá ukazatel rozhraní na enumerátor, který obsahuje `mdFile` tokeny souborů, na které se odkazuje sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="0ac36-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="0ac36-115">EnumManifestResources – metoda</span><span class="sxs-lookup"><span data-stu-id="0ac36-115">EnumManifestResources Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="0ac36-116">Získá ukazatel rozhraní na enumerátor, který obsahuje `mdManifestResource` tokeny prostředků, na které se odkazuje sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="0ac36-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="0ac36-117">FindAssembliesByName – metoda</span><span class="sxs-lookup"><span data-stu-id="0ac36-117">FindAssembliesByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="0ac36-118">Získá pole `mdAssemblyRef`ch tokenů pro sestavení se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="0ac36-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="0ac36-119">FindExportedTypeByName – metoda</span><span class="sxs-lookup"><span data-stu-id="0ac36-119">FindExportedTypeByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="0ac36-120">Získá token `mdExportedType` pro typ COM se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="0ac36-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="0ac36-121">FindManifestResourceByName – metoda</span><span class="sxs-lookup"><span data-stu-id="0ac36-121">FindManifestResourceByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="0ac36-122">Získá token `mdManifestResource` pro prostředek se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="0ac36-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="0ac36-123">GetAssemblyFromScope – metoda</span><span class="sxs-lookup"><span data-stu-id="0ac36-123">GetAssemblyFromScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="0ac36-124">Získá token pro sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="0ac36-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="0ac36-125">GetAssemblyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="0ac36-125">GetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="0ac36-126">Získá nastavení vlastností zadaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="0ac36-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="0ac36-127">GetAssemblyRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="0ac36-127">GetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="0ac36-128">Získá nastavení vlastností zadaného tokenu `mdAssemblyRef`.</span><span class="sxs-lookup"><span data-stu-id="0ac36-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="0ac36-129">GetExportedTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="0ac36-129">GetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="0ac36-130">Získá nastavení vlastností zadaného typu modelu COM.</span><span class="sxs-lookup"><span data-stu-id="0ac36-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="0ac36-131">GetFileProps – metoda</span><span class="sxs-lookup"><span data-stu-id="0ac36-131">GetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="0ac36-132">Získá nastavení vlastností zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="0ac36-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="0ac36-133">GetManifestResourceProps – metoda</span><span class="sxs-lookup"><span data-stu-id="0ac36-133">GetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="0ac36-134">Získá nastavení vlastností zadaného prostředku manifestu.</span><span class="sxs-lookup"><span data-stu-id="0ac36-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0ac36-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ac36-135">Requirements</span></span>  
 <span data-ttu-id="0ac36-136">**Platforma:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ac36-136">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ac36-137">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0ac36-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0ac36-138">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="0ac36-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0ac36-139">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ac36-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ac36-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ac36-140">See also</span></span>

- [<span data-ttu-id="0ac36-141">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="0ac36-141">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="0ac36-142">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ac36-142">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
