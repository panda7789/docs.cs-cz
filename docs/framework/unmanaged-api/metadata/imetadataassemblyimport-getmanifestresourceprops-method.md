---
title: "IMetaDataAssemblyImport::GetManifestResourceProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetManifestResourceProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ba9af4abca111b94a678c48d236a53dc6313b21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="82e88-102">IMetaDataAssemblyImport::GetManifestResourceProps – metoda</span><span class="sxs-lookup"><span data-stu-id="82e88-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>
<span data-ttu-id="82e88-103">Získá sadu vlastností prostředku manifestu podpisem Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="82e88-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82e88-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82e88-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="82e88-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="82e88-105">Parameters</span></span>  
 `mdmr`  
 <span data-ttu-id="82e88-106">[v] `mdManifestResource` Token, který představuje prostředků, pro které chcete získat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="82e88-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="82e88-107">[out] Název prostředku.</span><span class="sxs-lookup"><span data-stu-id="82e88-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="82e88-108">[v] Velikost v široké znaků, z `szName`.</span><span class="sxs-lookup"><span data-stu-id="82e88-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="82e88-109">[out] Ukazatel na počet široké znaků ve skutečnosti, vrátí se v `szName`.</span><span class="sxs-lookup"><span data-stu-id="82e88-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="82e88-110">[out] Ukazatel na `mdFile` tokenu nebo `mdAssemblyRef` token, který představuje soubor nebo sestavení, v uvedeném pořadí, který obsahuje prostředek.</span><span class="sxs-lookup"><span data-stu-id="82e88-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="82e88-111">[out] Ukazatel na hodnotu, která určuje posun na začátek prostředků v rámci tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="82e88-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="82e88-112">[out] Ukazatel na příznaky, které popisují metadata u prostředku.</span><span class="sxs-lookup"><span data-stu-id="82e88-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="82e88-113">Hodnota příznaky je kombinací jednoho nebo více [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) hodnoty.</span><span class="sxs-lookup"><span data-stu-id="82e88-113">The flags value is a combination of one or more [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82e88-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="82e88-114">Requirements</span></span>  
 <span data-ttu-id="82e88-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82e88-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82e88-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="82e88-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="82e88-117">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="82e88-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="82e88-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82e88-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e88-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="82e88-119">See Also</span></span>  
 [<span data-ttu-id="82e88-120">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82e88-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
