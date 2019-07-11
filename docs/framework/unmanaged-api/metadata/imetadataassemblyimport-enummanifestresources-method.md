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
ms.openlocfilehash: 717682bdcb2409a5f58f040a3ac2eafd73f01f7e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777952"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="88068-102">IMetaDataAssemblyImport::EnumManifestResources – metoda</span><span class="sxs-lookup"><span data-stu-id="88068-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="88068-103">Získá ukazatel na enumerátor pro prostředky odkazovat v aktuálním manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="88068-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88068-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88068-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,   
    [out] mdManifestResource   rManifestResources[],   
    [in]  ULONG                cMax,   
    [out] ULONG                *pcTokens  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="88068-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="88068-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="88068-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="88068-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="88068-107">Musí se jednat s hodnotou null hodnotu v případě `EnumManifestResources` je metoda volána poprvé.</span><span class="sxs-lookup"><span data-stu-id="88068-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="88068-108">[out] Pole používá k ukládání `mdManifestResource` tokeny metadat.</span><span class="sxs-lookup"><span data-stu-id="88068-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="88068-109">[in] Maximální počet `mdManifestResource` tokeny, které mohou být umístěny v `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="88068-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="88068-110">[out] Počet `mdManifestResource` tokeny ve skutečnosti umístěny do `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="88068-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88068-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="88068-111">Return Value</span></span>  
  
|<span data-ttu-id="88068-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="88068-112">HRESULT</span></span>|<span data-ttu-id="88068-113">Popis</span><span class="sxs-lookup"><span data-stu-id="88068-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="88068-114">`EnumManifestResources` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="88068-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="88068-115">Neexistují žádné tokeny se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="88068-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="88068-116">V takovém případě `pcTokens` je nastavena na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="88068-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="88068-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="88068-117">Requirements</span></span>  
 <span data-ttu-id="88068-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88068-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88068-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="88068-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="88068-120">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="88068-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="88068-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88068-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88068-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="88068-122">See also</span></span>

- [<span data-ttu-id="88068-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="88068-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
