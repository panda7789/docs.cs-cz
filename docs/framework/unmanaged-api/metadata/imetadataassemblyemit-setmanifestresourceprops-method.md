---
title: "IMetaDataAssemblyEmit::SetManifestResourceProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetManifestResourceProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetManifestResourceProps
helpviewer_keywords:
- SetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetManifestResourceProps method [.NET Framework metadata]
ms.assetid: ef77efd1-849c-4e51-ba92-7ee3d2bf0339
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e3cc447b18ac6ccabd642ab0a1fb5b887fb4fbe4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="b3ac3-102">IMetaDataAssemblyEmit::SetManifestResourceProps – metoda</span><span class="sxs-lookup"><span data-stu-id="b3ac3-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="b3ac3-103">Upraví zadaný `ManifestResource` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="b3ac3-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3ac3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3ac3-104">Syntax</span></span>  
  
```  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,   
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b3ac3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b3ac3-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="b3ac3-106">[v] Token, který určuje `ManifestResource` strukturu metadat má být změněn.</span><span class="sxs-lookup"><span data-stu-id="b3ac3-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="b3ac3-107">[v] Token, typu `File` nebo `AssemblyRef`, která se mapuje na zprostředkovateli prostředků.</span><span class="sxs-lookup"><span data-stu-id="b3ac3-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="b3ac3-108">[v] Posun na začátek prostředků v rámci tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="b3ac3-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="b3ac3-109">[v] Bitová kombinace hodnot příznaku, které určují atributy prostředku.</span><span class="sxs-lookup"><span data-stu-id="b3ac3-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3ac3-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3ac3-110">Remarks</span></span>  
 <span data-ttu-id="b3ac3-111">Chcete-li vytvořit `ManifestResource` strukturu metadat, použijte [imetadataassemblyemit::definemanifestresource –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="b3ac3-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3ac3-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b3ac3-112">Requirements</span></span>  
 <span data-ttu-id="b3ac3-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3ac3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3ac3-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b3ac3-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b3ac3-115">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b3ac3-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b3ac3-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3ac3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3ac3-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3ac3-117">See Also</span></span>  
 [<span data-ttu-id="b3ac3-118">Imetadataassemblyemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3ac3-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
