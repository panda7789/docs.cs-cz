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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905226"
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="7f322-102">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f322-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="7f322-103">Poskytuje metody, které podporují vlastní popis modelu používá modul common language runtime řešení a využívat prostředky.</span><span class="sxs-lookup"><span data-stu-id="7f322-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7f322-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7f322-104">Methods</span></span>  
  
|<span data-ttu-id="7f322-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7f322-105">Method</span></span>|<span data-ttu-id="7f322-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7f322-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7f322-107">DefineAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="7f322-107">DefineAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="7f322-108">Vytvoří strukturu dat sestavení obsahující metadata pro zadané sestavení a vrátí token metadat.</span><span class="sxs-lookup"><span data-stu-id="7f322-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="7f322-109">DefineAssemblyRef – metoda</span><span class="sxs-lookup"><span data-stu-id="7f322-109">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="7f322-110">Vytvoří `AssemblyRef` struktura obsahující metadata pro sestavení, které toto sestavení odkazuje a vrátí token metadat.</span><span class="sxs-lookup"><span data-stu-id="7f322-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="7f322-111">DefineExportedType – metoda</span><span class="sxs-lookup"><span data-stu-id="7f322-111">DefineExportedType Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="7f322-112">Vytvoří `ExportedType` struktura obsahující metadata pro zadanou exportovat typ a vrátí token metadat.</span><span class="sxs-lookup"><span data-stu-id="7f322-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="7f322-113">DefineFile – metoda</span><span class="sxs-lookup"><span data-stu-id="7f322-113">DefineFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="7f322-114">Vytvoří `File` struktury metadat obsahující metadata pro sestavení odkazuje toto sestavení a vrátí token metadat.</span><span class="sxs-lookup"><span data-stu-id="7f322-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="7f322-115">DefineManifestResource – metoda</span><span class="sxs-lookup"><span data-stu-id="7f322-115">DefineManifestResource Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="7f322-116">Vytvoří `ManifestResource` struktury obsahující metadata pro zadaný prostředek manifestu a vrátí token metadat.</span><span class="sxs-lookup"><span data-stu-id="7f322-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="7f322-117">SetAssemblyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="7f322-117">SetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="7f322-118">Upraví zadaný `Assembly` struktury metadat.</span><span class="sxs-lookup"><span data-stu-id="7f322-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="7f322-119">SetAssemblyRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="7f322-119">SetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="7f322-120">Upraví zadaný `AssemblyRef` struktury metadat.</span><span class="sxs-lookup"><span data-stu-id="7f322-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="7f322-121">SetExportedTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="7f322-121">SetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="7f322-122">Upraví zadaný `ExportedType` struktury metadat.</span><span class="sxs-lookup"><span data-stu-id="7f322-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="7f322-123">SetFileProps – metoda</span><span class="sxs-lookup"><span data-stu-id="7f322-123">SetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="7f322-124">Upraví zadaný `File` struktury metadat.</span><span class="sxs-lookup"><span data-stu-id="7f322-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="7f322-125">SetManifestResourceProps – metoda</span><span class="sxs-lookup"><span data-stu-id="7f322-125">SetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="7f322-126">Upraví zadaný `ManifestResource` struktury metadat.</span><span class="sxs-lookup"><span data-stu-id="7f322-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f322-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f322-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f322-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f322-128">Requirements</span></span>  
 <span data-ttu-id="7f322-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f322-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f322-130">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7f322-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f322-131">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7f322-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7f322-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f322-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f322-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f322-133">See also</span></span>

- [<span data-ttu-id="7f322-134">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="7f322-134">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="7f322-135">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f322-135">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
