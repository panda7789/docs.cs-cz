---
title: IMetaDataAssemblyImport::GetManifestResourceProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ba99d84686974b425bcdee0bbf4770e4843e1351
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081655"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="fc415-102">IMetaDataAssemblyImport::GetManifestResourceProps – metoda</span><span class="sxs-lookup"><span data-stu-id="fc415-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>
<span data-ttu-id="fc415-103">Získá sadu vlastností prostředku manifestu podpisem Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="fc415-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc415-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc415-104">Syntax</span></span>  
  
```  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] mdToken              *ptkImplementation,   
    [out] DWORD                *pdwOffset,   
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc415-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc415-105">Parameters</span></span>  
 `mdmr`  
 <span data-ttu-id="fc415-106">[in] `mdManifestResource` Token, který představuje prostředek, pro které chcete získat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="fc415-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="fc415-107">[out] Název prostředku.</span><span class="sxs-lookup"><span data-stu-id="fc415-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="fc415-108">[in] Velikost v široké znaky z `szName`.</span><span class="sxs-lookup"><span data-stu-id="fc415-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="fc415-109">[out] Ukazatel na počet skutečně vrácených v široké znaky `szName`.</span><span class="sxs-lookup"><span data-stu-id="fc415-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="fc415-110">[out] Ukazatel `mdFile` token nebo `mdAssemblyRef` token představující soubor nebo sestavení, v uvedeném pořadí, který obsahuje prostředek.</span><span class="sxs-lookup"><span data-stu-id="fc415-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="fc415-111">[out] Ukazatel na hodnotu, která určuje posun na začátek prostředků v rámci souboru.</span><span class="sxs-lookup"><span data-stu-id="fc415-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="fc415-112">[out] Ukazatel na příznaky, které popisují metadata pro prostředek použito.</span><span class="sxs-lookup"><span data-stu-id="fc415-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="fc415-113">Hodnota příznaků je kombinace jedné nebo více [cormanifestresourceflags –](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) hodnoty.</span><span class="sxs-lookup"><span data-stu-id="fc415-113">The flags value is a combination of one or more [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc415-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fc415-114">Requirements</span></span>  
 <span data-ttu-id="fc415-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc415-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc415-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fc415-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fc415-117">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fc415-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="fc415-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="fc415-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fc415-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc415-119">See also</span></span>

- [<span data-ttu-id="fc415-120">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fc415-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
