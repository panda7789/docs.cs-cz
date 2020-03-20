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
ms.openlocfilehash: 9370b27fd385b0223b354365d64aa57048f4ec69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177842"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="96011-102">IMetaDataAssemblyEmit::SetManifestResourceProps – metoda</span><span class="sxs-lookup"><span data-stu-id="96011-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="96011-103">Upraví zadanou `ManifestResource` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="96011-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96011-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96011-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96011-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="96011-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="96011-106">[v] Token, který určuje `ManifestResource` strukturu metadat, která má být změněna.</span><span class="sxs-lookup"><span data-stu-id="96011-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="96011-107">[v] Token typu `File` nebo `AssemblyRef`, který se mapuje na poskytovatele prostředků.</span><span class="sxs-lookup"><span data-stu-id="96011-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="96011-108">[v] Posun na začátek prostředku v souboru.</span><span class="sxs-lookup"><span data-stu-id="96011-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="96011-109">[v] Bitová kombinace hodnot příznaku, které určují atributy prostředku.</span><span class="sxs-lookup"><span data-stu-id="96011-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96011-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96011-110">Remarks</span></span>  
 <span data-ttu-id="96011-111">Chcete-li `ManifestResource` vytvořit strukturu metadat, použijte metodu [IMetaDataAssemblyEmit::DefineManifestResource.](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)</span><span class="sxs-lookup"><span data-stu-id="96011-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96011-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="96011-112">Requirements</span></span>  
 <span data-ttu-id="96011-113">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96011-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96011-114">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="96011-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96011-115">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="96011-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="96011-116">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96011-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96011-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="96011-117">See also</span></span>

- [<span data-ttu-id="96011-118">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96011-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
