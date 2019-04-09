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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7abcb7b69d0f0f2c53cd236c9b4092a94e0f421c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110674"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="8799d-102">IMetaDataAssemblyImport::EnumManifestResources – metoda</span><span class="sxs-lookup"><span data-stu-id="8799d-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="8799d-103">Získá ukazatel na enumerátor pro prostředky odkazovat v aktuálním manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="8799d-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8799d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8799d-104">Syntax</span></span>  
  
```  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,   
    [out] mdManifestResource   rManifestResources[],   
    [in]  ULONG                cMax,   
    [out] ULONG                *pcTokens  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="8799d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8799d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="8799d-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="8799d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="8799d-107">Musí se jednat s hodnotou null hodnotu v případě `EnumManifestResources` je metoda volána poprvé.</span><span class="sxs-lookup"><span data-stu-id="8799d-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="8799d-108">[out] Pole používá k ukládání `mdManifestResource` tokeny metadat.</span><span class="sxs-lookup"><span data-stu-id="8799d-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8799d-109">[in] Maximální počet `mdManifestResource` tokeny, které mohou být umístěny v `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="8799d-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="8799d-110">[out] Počet `mdManifestResource` tokeny ve skutečnosti umístěny do `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="8799d-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8799d-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8799d-111">Return Value</span></span>  
  
|<span data-ttu-id="8799d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8799d-112">HRESULT</span></span>|<span data-ttu-id="8799d-113">Popis</span><span class="sxs-lookup"><span data-stu-id="8799d-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumManifestResources` <span data-ttu-id="8799d-114">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="8799d-114">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8799d-115">Neexistují žádné tokeny se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="8799d-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="8799d-116">V takovém případě `pcTokens` je nastavena na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="8799d-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8799d-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8799d-117">Requirements</span></span>  
 <span data-ttu-id="8799d-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8799d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8799d-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8799d-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8799d-120">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8799d-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="8799d-121">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="8799d-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8799d-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8799d-122">See also</span></span>

- [<span data-ttu-id="8799d-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8799d-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
