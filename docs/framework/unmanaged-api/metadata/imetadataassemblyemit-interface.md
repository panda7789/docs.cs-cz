---
title: IMetaDataAssemblyEmit – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit
helpviewer_keywords:
- IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bda949db469d4b8629e54c9e5907da23ac7e169b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449374"
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="bd8bc-102">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd8bc-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="bd8bc-103">Poskytuje metody, které podporují vlastní popis modelu používaný modul common language runtime řešení a využívat prostředky.</span><span class="sxs-lookup"><span data-stu-id="bd8bc-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bd8bc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bd8bc-104">Methods</span></span>  
  
|<span data-ttu-id="bd8bc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bd8bc-105">Method</span></span>|<span data-ttu-id="bd8bc-106">Popis</span><span class="sxs-lookup"><span data-stu-id="bd8bc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bd8bc-107">DefineAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="bd8bc-107">DefineAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="bd8bc-108">Vytvoří strukturu dat sestavení obsahující metadata pro zadaného sestavení a vrátí token přidružených metadat.</span><span class="sxs-lookup"><span data-stu-id="bd8bc-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="bd8bc-109">DefineAssemblyRef – metoda</span><span class="sxs-lookup"><span data-stu-id="bd8bc-109">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="bd8bc-110">Vytvoří `AssemblyRef` struktura obsahující metadata pro sestavení, které toto sestavení odkazuje a vrátí token přidružených metadat.</span><span class="sxs-lookup"><span data-stu-id="bd8bc-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="bd8bc-111">DefineExportedType – metoda</span><span class="sxs-lookup"><span data-stu-id="bd8bc-111">DefineExportedType Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="bd8bc-112">Vytvoří `ExportedType` struktura obsahující metadata pro zadaný typ exportovat a vrátí token přidružených metadat.</span><span class="sxs-lookup"><span data-stu-id="bd8bc-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="bd8bc-113">DefineFile – metoda</span><span class="sxs-lookup"><span data-stu-id="bd8bc-113">DefineFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="bd8bc-114">Vytvoří `File` strukturu metadat obsahující metadata pro sestavení odkazuje toto sestavení a vrátí token přidružených metadat.</span><span class="sxs-lookup"><span data-stu-id="bd8bc-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="bd8bc-115">DefineManifestResource – metoda</span><span class="sxs-lookup"><span data-stu-id="bd8bc-115">DefineManifestResource Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="bd8bc-116">Vytvoří `ManifestResource` struktury obsahující metadata pro zadanou prostředku manifestu a vrátí token přidružených metadat.</span><span class="sxs-lookup"><span data-stu-id="bd8bc-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="bd8bc-117">SetAssemblyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="bd8bc-117">SetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="bd8bc-118">Upraví zadaný `Assembly` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="bd8bc-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="bd8bc-119">SetAssemblyRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="bd8bc-119">SetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="bd8bc-120">Upraví zadaný `AssemblyRef` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="bd8bc-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="bd8bc-121">SetExportedTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="bd8bc-121">SetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="bd8bc-122">Upraví zadaný `ExportedType` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="bd8bc-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="bd8bc-123">SetFileProps – metoda</span><span class="sxs-lookup"><span data-stu-id="bd8bc-123">SetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="bd8bc-124">Upraví zadaný `File` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="bd8bc-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="bd8bc-125">SetManifestResourceProps – metoda</span><span class="sxs-lookup"><span data-stu-id="bd8bc-125">SetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="bd8bc-126">Upraví zadaný `ManifestResource` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="bd8bc-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd8bc-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bd8bc-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd8bc-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bd8bc-128">Requirements</span></span>  
 <span data-ttu-id="bd8bc-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd8bc-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd8bc-130">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bd8bc-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bd8bc-131">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bd8bc-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bd8bc-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd8bc-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd8bc-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd8bc-133">See Also</span></span>  
 [<span data-ttu-id="bd8bc-134">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="bd8bc-134">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="bd8bc-135">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd8bc-135">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
