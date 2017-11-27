---
title: "IMetaDataAssemblyEmit – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit
helpviewer_keywords: IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: af7a5fd5a564aa7366924f47b0c526aff7153521
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="5d747-102">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d747-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="5d747-103">Poskytuje metody, které podporují vlastní popis modelu používaný modul common language runtime řešení a využívat prostředky.</span><span class="sxs-lookup"><span data-stu-id="5d747-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5d747-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5d747-104">Methods</span></span>  
  
|<span data-ttu-id="5d747-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5d747-105">Method</span></span>|<span data-ttu-id="5d747-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5d747-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5d747-107">Defineassembly – metoda</span><span class="sxs-lookup"><span data-stu-id="5d747-107">DefineAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="5d747-108">Vytvoří strukturu dat sestavení obsahující metadata pro zadaného sestavení a vrátí token přidružených metadat.</span><span class="sxs-lookup"><span data-stu-id="5d747-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="5d747-109">Defineassemblyref – metoda</span><span class="sxs-lookup"><span data-stu-id="5d747-109">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="5d747-110">Vytvoří `AssemblyRef` struktura obsahující metadata pro sestavení, které toto sestavení odkazuje a vrátí token přidružených metadat.</span><span class="sxs-lookup"><span data-stu-id="5d747-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="5d747-111">Defineexportedtype – metoda</span><span class="sxs-lookup"><span data-stu-id="5d747-111">DefineExportedType Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="5d747-112">Vytvoří `ExportedType` struktura obsahující metadata pro zadaný typ exportovat a vrátí token přidružených metadat.</span><span class="sxs-lookup"><span data-stu-id="5d747-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="5d747-113">Definefile – metoda</span><span class="sxs-lookup"><span data-stu-id="5d747-113">DefineFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="5d747-114">Vytvoří `File` strukturu metadat obsahující metadata pro sestavení odkazuje toto sestavení a vrátí token přidružených metadat.</span><span class="sxs-lookup"><span data-stu-id="5d747-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="5d747-115">DefineManifestResource – metoda</span><span class="sxs-lookup"><span data-stu-id="5d747-115">DefineManifestResource Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="5d747-116">Vytvoří `ManifestResource` struktury obsahující metadata pro zadanou prostředku manifestu a vrátí token přidružených metadat.</span><span class="sxs-lookup"><span data-stu-id="5d747-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="5d747-117">Setassemblyprops – metoda</span><span class="sxs-lookup"><span data-stu-id="5d747-117">SetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="5d747-118">Upraví zadaný `Assembly` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="5d747-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="5d747-119">Setassemblyrefprops – metoda</span><span class="sxs-lookup"><span data-stu-id="5d747-119">SetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="5d747-120">Upraví zadaný `AssemblyRef` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="5d747-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="5d747-121">Setexportedtypeprops – metoda</span><span class="sxs-lookup"><span data-stu-id="5d747-121">SetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="5d747-122">Upraví zadaný `ExportedType` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="5d747-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="5d747-123">Setfileprops – metoda</span><span class="sxs-lookup"><span data-stu-id="5d747-123">SetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="5d747-124">Upraví zadaný `File` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="5d747-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="5d747-125">Setmanifestresourceprops – metoda</span><span class="sxs-lookup"><span data-stu-id="5d747-125">SetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="5d747-126">Upraví zadaný `ManifestResource` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="5d747-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d747-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5d747-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d747-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5d747-128">Requirements</span></span>  
 <span data-ttu-id="5d747-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d747-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d747-130">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5d747-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5d747-131">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5d747-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5d747-132">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d747-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d747-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d747-133">See Also</span></span>  
 [<span data-ttu-id="5d747-134">Rozhraní metadat</span><span class="sxs-lookup"><span data-stu-id="5d747-134">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="5d747-135">Imetadataassemblyimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d747-135">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
