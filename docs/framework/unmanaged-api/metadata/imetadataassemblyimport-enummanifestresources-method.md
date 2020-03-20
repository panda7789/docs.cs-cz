---
title: IMetaDataAssemblyImport::EnumManifestResources – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumManifestResources
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumManifestResources
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumManifestResources method [.NET Framework metadata]
- EnumManifestResources method [.NET Framework metadata]
ms.assetid: 9543b111-5705-40c9-935c-a3ffc7a581aa
topic_type:
- apiref
ms.openlocfilehash: 22141cf46a965c0624c076bd1d86d2624e5a09f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176016"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="1223e-102">IMetaDataAssemblyImport::EnumManifestResources – metoda</span><span class="sxs-lookup"><span data-stu-id="1223e-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="1223e-103">Získá ukazatel výčtu pro prostředky odkazuje v aktuálnímanifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="1223e-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1223e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1223e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,
    [out] mdManifestResource   rManifestResources[],
    [in]  ULONG                cMax,
    [out] ULONG                *pcTokens  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="1223e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1223e-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="1223e-106">[dovnitř, ven] Ukazatel na čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="1223e-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="1223e-107">To musí být hodnota `EnumManifestResources` null při první volání metody.</span><span class="sxs-lookup"><span data-stu-id="1223e-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="1223e-108">[out] Pole používané k `mdManifestResource` ukládání tokenů metadat.</span><span class="sxs-lookup"><span data-stu-id="1223e-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1223e-109">[v] Maximální počet `mdManifestResource` tokenů, které mohou `rManifestResources`být umístěny v .</span><span class="sxs-lookup"><span data-stu-id="1223e-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="1223e-110">[out] Počet tokenů `mdManifestResource` skutečně umístěných v `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="1223e-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1223e-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1223e-111">Return Value</span></span>  
  
|<span data-ttu-id="1223e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1223e-112">HRESULT</span></span>|<span data-ttu-id="1223e-113">Popis</span><span class="sxs-lookup"><span data-stu-id="1223e-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1223e-114">`EnumManifestResources`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="1223e-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="1223e-115">Neexistují žádné tokeny výčet.</span><span class="sxs-lookup"><span data-stu-id="1223e-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="1223e-116">V tomto `pcTokens` případě je nastavena na nulu.</span><span class="sxs-lookup"><span data-stu-id="1223e-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1223e-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1223e-117">Requirements</span></span>  
 <span data-ttu-id="1223e-118">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1223e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1223e-119">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="1223e-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1223e-120">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1223e-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1223e-121">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1223e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1223e-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="1223e-122">See also</span></span>

- [<span data-ttu-id="1223e-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1223e-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
