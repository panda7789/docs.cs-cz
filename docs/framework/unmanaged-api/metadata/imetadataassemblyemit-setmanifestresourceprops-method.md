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
ms.openlocfilehash: d92129bd7c51ba2fa574f8337ba2b3727ab7b172
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599046"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="082e6-102">IMetaDataAssemblyEmit::SetManifestResourceProps – metoda</span><span class="sxs-lookup"><span data-stu-id="082e6-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="082e6-103">Upraví zadaný `ManifestResource` struktury metadat.</span><span class="sxs-lookup"><span data-stu-id="082e6-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="082e6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="082e6-104">Syntax</span></span>  
  
```  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,   
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="082e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="082e6-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="082e6-106">[in] Token, který určuje, `ManifestResource` struktury metadat má být upraven.</span><span class="sxs-lookup"><span data-stu-id="082e6-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="082e6-107">[in] Token typu `File` nebo `AssemblyRef`, který se mapuje na poskytovateli prostředků.</span><span class="sxs-lookup"><span data-stu-id="082e6-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="082e6-108">[in] Posun k začátku prostředků v rámci souboru.</span><span class="sxs-lookup"><span data-stu-id="082e6-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="082e6-109">[in] Bitová kombinace hodnot příznaků, které určují atributy prostředku.</span><span class="sxs-lookup"><span data-stu-id="082e6-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="082e6-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="082e6-110">Remarks</span></span>  
 <span data-ttu-id="082e6-111">Vytvoření `ManifestResource` struktury metadat, použijte [imetadataassemblyemit::definemanifestresource –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="082e6-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="082e6-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="082e6-112">Requirements</span></span>  
 <span data-ttu-id="082e6-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="082e6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="082e6-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="082e6-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="082e6-115">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="082e6-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="082e6-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="082e6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="082e6-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="082e6-117">See also</span></span>
- [<span data-ttu-id="082e6-118">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="082e6-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
