---
title: "IMetaDataAssemblyImport::EnumManifestResources – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.EnumManifestResources
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::EnumManifestResources
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumManifestResources method [.NET Framework metadata]
- EnumManifestResources method [.NET Framework metadata]
ms.assetid: 9543b111-5705-40c9-935c-a3ffc7a581aa
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 25d8b63e2f40566164274715e562960eafbb83e5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="3ba6e-102">IMetaDataAssemblyImport::EnumManifestResources – metoda</span><span class="sxs-lookup"><span data-stu-id="3ba6e-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="3ba6e-103">Získá ukazatel na enumerátor pro prostředky v aktuální manifest sestavení odkazuje.</span><span class="sxs-lookup"><span data-stu-id="3ba6e-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ba6e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ba6e-104">Syntax</span></span>  
  
```  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,   
    [out] mdManifestResource   rManifestResources[],   
    [in]  ULONG                cMax,   
    [out] ULONG                *pcTokens  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="3ba6e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ba6e-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3ba6e-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="3ba6e-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="3ba6e-107">Tato hodnota musí být null hodnotu v případě `EnumManifestResources` metoda je volána poprvé.</span><span class="sxs-lookup"><span data-stu-id="3ba6e-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="3ba6e-108">[out] Pole používá k ukládání `mdManifestResource` tokenů metadat.</span><span class="sxs-lookup"><span data-stu-id="3ba6e-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3ba6e-109">[v] Maximální počet `mdManifestResource` tokeny, které mohou být umístěny v `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="3ba6e-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="3ba6e-110">[out] Počet `mdManifestResource` tokeny umístěna v `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="3ba6e-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ba6e-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3ba6e-111">Return Value</span></span>  
  
|<span data-ttu-id="3ba6e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3ba6e-112">HRESULT</span></span>|<span data-ttu-id="3ba6e-113">Popis</span><span class="sxs-lookup"><span data-stu-id="3ba6e-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3ba6e-114">`EnumManifestResources`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="3ba6e-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3ba6e-115">Neexistují žádné tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="3ba6e-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="3ba6e-116">V takovém případě `pcTokens` je nastaven na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="3ba6e-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3ba6e-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3ba6e-117">Requirements</span></span>  
 <span data-ttu-id="3ba6e-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ba6e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ba6e-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3ba6e-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3ba6e-120">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3ba6e-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3ba6e-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ba6e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ba6e-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ba6e-122">See Also</span></span>  
 [<span data-ttu-id="3ba6e-123">Imetadataassemblyimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3ba6e-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
