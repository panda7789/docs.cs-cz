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
ms.openlocfilehash: 74111a175b0decbc1beef7c8df5ade59d31d845b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009142"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="5fcd2-102">IMetaDataAssemblyEmit::SetManifestResourceProps – metoda</span><span class="sxs-lookup"><span data-stu-id="5fcd2-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="5fcd2-103">Upraví zadanou `ManifestResource` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="5fcd2-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fcd2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5fcd2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fcd2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5fcd2-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="5fcd2-106">pro Token, který určuje `ManifestResource` strukturu metadat, která má být upravena.</span><span class="sxs-lookup"><span data-stu-id="5fcd2-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="5fcd2-107">pro Token typu `File` nebo `AssemblyRef` , který se mapuje na poskytovatele prostředků.</span><span class="sxs-lookup"><span data-stu-id="5fcd2-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="5fcd2-108">pro Posun na začátek prostředku v rámci souboru.</span><span class="sxs-lookup"><span data-stu-id="5fcd2-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="5fcd2-109">pro Bitová kombinace hodnot příznaků, které určují atributy prostředku.</span><span class="sxs-lookup"><span data-stu-id="5fcd2-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fcd2-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5fcd2-110">Remarks</span></span>  
 <span data-ttu-id="5fcd2-111">Chcete-li vytvořit `ManifestResource` strukturu metadat, použijte metodu [IMetaDataAssemblyEmit::D efinemanifestresource](imetadataassemblyemit-definemanifestresource-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5fcd2-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fcd2-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5fcd2-112">Requirements</span></span>  
 <span data-ttu-id="5fcd2-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fcd2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fcd2-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5fcd2-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5fcd2-115">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="5fcd2-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5fcd2-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fcd2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fcd2-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="5fcd2-117">See also</span></span>

- [<span data-ttu-id="5fcd2-118">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5fcd2-118">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
