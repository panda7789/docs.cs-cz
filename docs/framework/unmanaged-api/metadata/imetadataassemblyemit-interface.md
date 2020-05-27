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
ms.openlocfilehash: 807e1ee831a43a4ef1e7b0a269ee38131f24081e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008115"
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="16f1f-102">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="16f1f-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="16f1f-103">Poskytuje metody, které podporují model s použitím společného jazykového modulu CLR k řešení a využívání prostředků.</span><span class="sxs-lookup"><span data-stu-id="16f1f-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="16f1f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="16f1f-104">Methods</span></span>  
  
|<span data-ttu-id="16f1f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="16f1f-105">Method</span></span>|<span data-ttu-id="16f1f-106">Description</span><span class="sxs-lookup"><span data-stu-id="16f1f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="16f1f-107">DefineAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="16f1f-107">DefineAssembly Method</span></span>](imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="16f1f-108">Vytvoří strukturu dat sestavení obsahující metadata pro zadané sestavení a vrátí přidružený token metadat.</span><span class="sxs-lookup"><span data-stu-id="16f1f-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="16f1f-109">DefineAssemblyRef – metoda</span><span class="sxs-lookup"><span data-stu-id="16f1f-109">DefineAssemblyRef Method</span></span>](imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="16f1f-110">Vytvoří `AssemblyRef` strukturu obsahující metadata pro sestavení, na které odkazuje toto sestavení, a vrátí přidružený token metadat.</span><span class="sxs-lookup"><span data-stu-id="16f1f-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="16f1f-111">DefineExportedType – metoda</span><span class="sxs-lookup"><span data-stu-id="16f1f-111">DefineExportedType Method</span></span>](imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="16f1f-112">Vytvoří `ExportedType` strukturu obsahující metadata pro zadaný exportovaný typ a vrátí přidružený token metadat.</span><span class="sxs-lookup"><span data-stu-id="16f1f-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="16f1f-113">DefineFile – metoda</span><span class="sxs-lookup"><span data-stu-id="16f1f-113">DefineFile Method</span></span>](imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="16f1f-114">Vytvoří `File` strukturu metadat obsahující metadata pro sestavení, na které odkazuje toto sestavení, a vrátí přidružený token metadat.</span><span class="sxs-lookup"><span data-stu-id="16f1f-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="16f1f-115">DefineManifestResource – metoda</span><span class="sxs-lookup"><span data-stu-id="16f1f-115">DefineManifestResource Method</span></span>](imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="16f1f-116">Vytvoří `ManifestResource` strukturu obsahující metadata pro zadaný prostředek manifestu a vrátí přidružený token metadat.</span><span class="sxs-lookup"><span data-stu-id="16f1f-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="16f1f-117">SetAssemblyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="16f1f-117">SetAssemblyProps Method</span></span>](imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="16f1f-118">Upraví zadanou `Assembly` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="16f1f-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="16f1f-119">SetAssemblyRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="16f1f-119">SetAssemblyRefProps Method</span></span>](imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="16f1f-120">Upraví zadanou `AssemblyRef` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="16f1f-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="16f1f-121">SetExportedTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="16f1f-121">SetExportedTypeProps Method</span></span>](imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="16f1f-122">Upraví zadanou `ExportedType` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="16f1f-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="16f1f-123">SetFileProps – metoda</span><span class="sxs-lookup"><span data-stu-id="16f1f-123">SetFileProps Method</span></span>](imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="16f1f-124">Upraví zadanou `File` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="16f1f-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="16f1f-125">SetManifestResourceProps – metoda</span><span class="sxs-lookup"><span data-stu-id="16f1f-125">SetManifestResourceProps Method</span></span>](imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="16f1f-126">Upraví zadanou `ManifestResource` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="16f1f-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16f1f-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="16f1f-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16f1f-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="16f1f-128">Requirements</span></span>  
 <span data-ttu-id="16f1f-129">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16f1f-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16f1f-130">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="16f1f-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="16f1f-131">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="16f1f-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="16f1f-132">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16f1f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16f1f-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="16f1f-133">See also</span></span>

- [<span data-ttu-id="16f1f-134">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="16f1f-134">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="16f1f-135">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="16f1f-135">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
