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
ms.openlocfilehash: 3a66ef090a205019493e099919739867e3936873
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081793"
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="ad044-102">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad044-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="ad044-103">Poskytuje metody, které podporují vlastní popis modelu používá modul common language runtime řešení a využívat prostředky.</span><span class="sxs-lookup"><span data-stu-id="ad044-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ad044-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ad044-104">Methods</span></span>  
  
|<span data-ttu-id="ad044-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ad044-105">Method</span></span>|<span data-ttu-id="ad044-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ad044-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ad044-107">DefineAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="ad044-107">DefineAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="ad044-108">Vytvoří strukturu dat sestavení obsahující metadata pro zadané sestavení a vrátí token metadat.</span><span class="sxs-lookup"><span data-stu-id="ad044-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="ad044-109">DefineAssemblyRef – metoda</span><span class="sxs-lookup"><span data-stu-id="ad044-109">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="ad044-110">Vytvoří `AssemblyRef` struktura obsahující metadata pro sestavení, které toto sestavení odkazuje a vrátí token metadat.</span><span class="sxs-lookup"><span data-stu-id="ad044-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="ad044-111">DefineExportedType – metoda</span><span class="sxs-lookup"><span data-stu-id="ad044-111">DefineExportedType Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="ad044-112">Vytvoří `ExportedType` struktura obsahující metadata pro zadanou exportovat typ a vrátí token metadat.</span><span class="sxs-lookup"><span data-stu-id="ad044-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="ad044-113">DefineFile – metoda</span><span class="sxs-lookup"><span data-stu-id="ad044-113">DefineFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="ad044-114">Vytvoří `File` struktury metadat obsahující metadata pro sestavení odkazuje toto sestavení a vrátí token metadat.</span><span class="sxs-lookup"><span data-stu-id="ad044-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="ad044-115">DefineManifestResource – metoda</span><span class="sxs-lookup"><span data-stu-id="ad044-115">DefineManifestResource Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="ad044-116">Vytvoří `ManifestResource` struktury obsahující metadata pro zadaný prostředek manifestu a vrátí token metadat.</span><span class="sxs-lookup"><span data-stu-id="ad044-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="ad044-117">SetAssemblyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="ad044-117">SetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="ad044-118">Upraví zadaný `Assembly` struktury metadat.</span><span class="sxs-lookup"><span data-stu-id="ad044-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="ad044-119">SetAssemblyRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="ad044-119">SetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="ad044-120">Upraví zadaný `AssemblyRef` struktury metadat.</span><span class="sxs-lookup"><span data-stu-id="ad044-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="ad044-121">SetExportedTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="ad044-121">SetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="ad044-122">Upraví zadaný `ExportedType` struktury metadat.</span><span class="sxs-lookup"><span data-stu-id="ad044-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="ad044-123">SetFileProps – metoda</span><span class="sxs-lookup"><span data-stu-id="ad044-123">SetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="ad044-124">Upraví zadaný `File` struktury metadat.</span><span class="sxs-lookup"><span data-stu-id="ad044-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="ad044-125">SetManifestResourceProps – metoda</span><span class="sxs-lookup"><span data-stu-id="ad044-125">SetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="ad044-126">Upraví zadaný `ManifestResource` struktury metadat.</span><span class="sxs-lookup"><span data-stu-id="ad044-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad044-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad044-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad044-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad044-128">Requirements</span></span>  
 <span data-ttu-id="ad044-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad044-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad044-130">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ad044-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ad044-131">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ad044-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="ad044-132">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ad044-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ad044-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad044-133">See also</span></span>

- [<span data-ttu-id="ad044-134">Rozhraní metadat</span><span class="sxs-lookup"><span data-stu-id="ad044-134">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="ad044-135">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad044-135">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
