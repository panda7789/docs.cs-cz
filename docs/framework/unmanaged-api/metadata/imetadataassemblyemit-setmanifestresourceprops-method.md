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
ms.openlocfilehash: f6b5e12df60663b75e10b04eaa008a75d720d753
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434439"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="4bf25-102">IMetaDataAssemblyEmit::SetManifestResourceProps – metoda</span><span class="sxs-lookup"><span data-stu-id="4bf25-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="4bf25-103">Upraví zadanou `ManifestResource` strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="4bf25-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bf25-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4bf25-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,   
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bf25-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4bf25-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="4bf25-106">pro Token, který určuje `ManifestResource` strukturu metadat k úpravě.</span><span class="sxs-lookup"><span data-stu-id="4bf25-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="4bf25-107">pro Token typu `File` nebo `AssemblyRef`, který se mapuje na poskytovatele prostředků.</span><span class="sxs-lookup"><span data-stu-id="4bf25-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="4bf25-108">pro Posun na začátek prostředku v rámci souboru.</span><span class="sxs-lookup"><span data-stu-id="4bf25-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="4bf25-109">pro Bitová kombinace hodnot příznaků, které určují atributy prostředku.</span><span class="sxs-lookup"><span data-stu-id="4bf25-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4bf25-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4bf25-110">Remarks</span></span>  
 <span data-ttu-id="4bf25-111">Chcete-li vytvořit `ManifestResource` struktury metadat, použijte metodu [IMetaDataAssemblyEmit::D efinemanifestresource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4bf25-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bf25-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4bf25-112">Requirements</span></span>  
 <span data-ttu-id="4bf25-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bf25-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bf25-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4bf25-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4bf25-115">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="4bf25-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4bf25-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bf25-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bf25-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4bf25-117">See also</span></span>

- [<span data-ttu-id="4bf25-118">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4bf25-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
