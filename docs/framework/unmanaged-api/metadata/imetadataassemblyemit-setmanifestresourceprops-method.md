---
title: IMetaDataAssemblyEmit::SetManifestResourceProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetManifestResourceProps
helpviewer_keywords:
- SetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetManifestResourceProps method [.NET Framework metadata]
ms.assetid: ef77efd1-849c-4e51-ba92-7ee3d2bf0339
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c6fbc3f41e95730e93bd907762dd8cd4205037c8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187301"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="c8ef7-102">IMetaDataAssemblyEmit::SetManifestResourceProps – metoda</span><span class="sxs-lookup"><span data-stu-id="c8ef7-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="c8ef7-103">Upraví zadaný `ManifestResource` struktury metadat.</span><span class="sxs-lookup"><span data-stu-id="c8ef7-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8ef7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8ef7-104">Syntax</span></span>  
  
```  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,   
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8ef7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c8ef7-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="c8ef7-106">[in] Token, který určuje, `ManifestResource` struktury metadat má být upraven.</span><span class="sxs-lookup"><span data-stu-id="c8ef7-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="c8ef7-107">[in] Token typu `File` nebo `AssemblyRef`, který se mapuje na poskytovateli prostředků.</span><span class="sxs-lookup"><span data-stu-id="c8ef7-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="c8ef7-108">[in] Posun k začátku prostředků v rámci souboru.</span><span class="sxs-lookup"><span data-stu-id="c8ef7-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="c8ef7-109">[in] Bitová kombinace hodnot příznaků, které určují atributy prostředku.</span><span class="sxs-lookup"><span data-stu-id="c8ef7-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8ef7-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c8ef7-110">Remarks</span></span>  
 <span data-ttu-id="c8ef7-111">Vytvoření `ManifestResource` struktury metadat, použijte [imetadataassemblyemit::definemanifestresource –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="c8ef7-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8ef7-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8ef7-112">Requirements</span></span>  
 <span data-ttu-id="c8ef7-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8ef7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8ef7-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c8ef7-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c8ef7-115">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c8ef7-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="c8ef7-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c8ef7-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c8ef7-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8ef7-117">See also</span></span>

- [<span data-ttu-id="c8ef7-118">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8ef7-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
