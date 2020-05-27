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
ms.openlocfilehash: 2a67f50fa1042e8d3957a9a0394507f260a328c6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009012"
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="5150a-102">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5150a-102">IMetaDataAssemblyImport Interface</span></span>
<span data-ttu-id="5150a-103">Poskytuje metody pro přístup k obsahu manifestu sestavení a jeho prohlížení.</span><span class="sxs-lookup"><span data-stu-id="5150a-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5150a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5150a-104">Methods</span></span>  
  
|<span data-ttu-id="5150a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5150a-105">Method</span></span>|<span data-ttu-id="5150a-106">Description</span><span class="sxs-lookup"><span data-stu-id="5150a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5150a-107">CloseEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="5150a-107">CloseEnum Method</span></span>](imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="5150a-108">Uvolní popisovač pro zadaný enumerátor.</span><span class="sxs-lookup"><span data-stu-id="5150a-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="5150a-109">EnumAssemblyRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="5150a-109">EnumAssemblyRefs Method</span></span>](imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="5150a-110">Získá ukazatel rozhraní na enumerátor, který obsahuje `mdAssemblyRef` tokeny sestavení odkazované sestavením v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="5150a-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="5150a-111">EnumExportedTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="5150a-111">EnumExportedTypes Method</span></span>](imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="5150a-112">Získá ukazatel rozhraní na enumerátor, který obsahuje `mdExportedType` tokeny typů com, na které odkazuje sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="5150a-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="5150a-113">EnumFiles – metoda</span><span class="sxs-lookup"><span data-stu-id="5150a-113">EnumFiles Method</span></span>](imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="5150a-114">Získá ukazatel rozhraní na enumerátor, který obsahuje `mdFile` tokeny souborů, na které odkazuje sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="5150a-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="5150a-115">EnumManifestResources – metoda</span><span class="sxs-lookup"><span data-stu-id="5150a-115">EnumManifestResources Method</span></span>](imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="5150a-116">Získá ukazatel rozhraní na enumerátor, který obsahuje `mdManifestResource` tokeny prostředků, na které se odkazuje v rámci sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="5150a-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="5150a-117">FindAssembliesByName – metoda</span><span class="sxs-lookup"><span data-stu-id="5150a-117">FindAssembliesByName Method</span></span>](imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="5150a-118">Získá pole `mdAssemblyRef` tokenů pro sestavení se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="5150a-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="5150a-119">FindExportedTypeByName – metoda</span><span class="sxs-lookup"><span data-stu-id="5150a-119">FindExportedTypeByName Method</span></span>](imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="5150a-120">Získá `mdExportedType` token pro typ com se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="5150a-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="5150a-121">FindManifestResourceByName – metoda</span><span class="sxs-lookup"><span data-stu-id="5150a-121">FindManifestResourceByName Method</span></span>](imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="5150a-122">Získá `mdManifestResource` token pro prostředek se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="5150a-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="5150a-123">GetAssemblyFromScope – metoda</span><span class="sxs-lookup"><span data-stu-id="5150a-123">GetAssemblyFromScope Method</span></span>](imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="5150a-124">Získá token pro sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="5150a-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="5150a-125">GetAssemblyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="5150a-125">GetAssemblyProps Method</span></span>](imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="5150a-126">Získá nastavení vlastností zadaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="5150a-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="5150a-127">GetAssemblyRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="5150a-127">GetAssemblyRefProps Method</span></span>](imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="5150a-128">Získá nastavení vlastností zadaného `mdAssemblyRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="5150a-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="5150a-129">GetExportedTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="5150a-129">GetExportedTypeProps Method</span></span>](imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="5150a-130">Získá nastavení vlastností zadaného typu modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5150a-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="5150a-131">GetFileProps – metoda</span><span class="sxs-lookup"><span data-stu-id="5150a-131">GetFileProps Method</span></span>](imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="5150a-132">Získá nastavení vlastností zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="5150a-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="5150a-133">GetManifestResourceProps – metoda</span><span class="sxs-lookup"><span data-stu-id="5150a-133">GetManifestResourceProps Method</span></span>](imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="5150a-134">Získá nastavení vlastností zadaného prostředku manifestu.</span><span class="sxs-lookup"><span data-stu-id="5150a-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5150a-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5150a-135">Requirements</span></span>  
 <span data-ttu-id="5150a-136">**Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5150a-136">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5150a-137">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5150a-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5150a-138">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="5150a-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5150a-139">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5150a-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5150a-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="5150a-140">See also</span></span>

- [<span data-ttu-id="5150a-141">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="5150a-141">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="5150a-142">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5150a-142">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
