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
ms.workload: dotnet
ms.openlocfilehash: 6a7e4bd68bfd985b8902ae3b2340773ca77eee10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="d355e-102">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d355e-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="d355e-103">Poskytuje metody, které podporují vlastní popis modelu používaný modul common language runtime řešení a využívat prostředky.</span><span class="sxs-lookup"><span data-stu-id="d355e-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d355e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d355e-104">Methods</span></span>  
  
|<span data-ttu-id="d355e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d355e-105">Method</span></span>|<span data-ttu-id="d355e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d355e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d355e-107">DefineAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="d355e-107">DefineAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="d355e-108">Vytvoří strukturu dat sestavení obsahující metadata pro zadaného sestavení a vrátí token přidružených metadat.</span><span class="sxs-lookup"><span data-stu-id="d355e-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="d355e-109">DefineAssemblyRef – metoda</span><span class="sxs-lookup"><span data-stu-id="d355e-109">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="d355e-110">Vytvoří `AssemblyRef` struktura obsahující metadata pro sestavení, které toto sestavení odkazuje a vrátí token přidružených metadat.</span><span class="sxs-lookup"><span data-stu-id="d355e-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="d355e-111">DefineExportedType – metoda</span><span class="sxs-lookup"><span data-stu-id="d355e-111">DefineExportedType Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="d355e-112">Vytvoří `ExportedType` struktura obsahující metadata pro zadaný typ exportovat a vrátí token přidružených metadat.</span><span class="sxs-lookup"><span data-stu-id="d355e-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="d355e-113">DefineFile – metoda</span><span class="sxs-lookup"><span data-stu-id="d355e-113">DefineFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="d355e-114">Vytvoří `File` strukturu metadat obsahující metadata pro sestavení odkazuje toto sestavení a vrátí token přidružených metadat.</span><span class="sxs-lookup"><span data-stu-id="d355e-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="d355e-115">DefineManifestResource – metoda</span><span class="sxs-lookup"><span data-stu-id="d355e-115">DefineManifestResource Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="d355e-116">Vytvoří `ManifestResource` struktury obsahující metadata pro zadanou prostředku manifestu a vrátí token přidružených metadat.</span><span class="sxs-lookup"><span data-stu-id="d355e-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="d355e-117">SetAssemblyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="d355e-117">SetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="d355e-118">Upraví zadaný `Assembly` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="d355e-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="d355e-119">SetAssemblyRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="d355e-119">SetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="d355e-120">Upraví zadaný `AssemblyRef` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="d355e-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="d355e-121">SetExportedTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="d355e-121">SetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="d355e-122">Upraví zadaný `ExportedType` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="d355e-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="d355e-123">SetFileProps – metoda</span><span class="sxs-lookup"><span data-stu-id="d355e-123">SetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="d355e-124">Upraví zadaný `File` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="d355e-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="d355e-125">SetManifestResourceProps – metoda</span><span class="sxs-lookup"><span data-stu-id="d355e-125">SetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="d355e-126">Upraví zadaný `ManifestResource` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="d355e-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d355e-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d355e-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d355e-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d355e-128">Requirements</span></span>  
 <span data-ttu-id="d355e-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d355e-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d355e-130">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d355e-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d355e-131">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d355e-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d355e-132">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d355e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d355e-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="d355e-133">See Also</span></span>  
 [<span data-ttu-id="d355e-134">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="d355e-134">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="d355e-135">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d355e-135">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
