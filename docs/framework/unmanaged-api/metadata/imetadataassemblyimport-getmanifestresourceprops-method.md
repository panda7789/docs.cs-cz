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
ms.openlocfilehash: d87d0d46ede65cf44c84edba92fe246174088a4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177658"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="c8491-102">IMetaDataAssemblyImport::GetManifestResourceProps – metoda</span><span class="sxs-lookup"><span data-stu-id="c8491-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>
<span data-ttu-id="c8491-103">Získá sadu vlastností prostředku manifestu se zadaným podpisem metadat.</span><span class="sxs-lookup"><span data-stu-id="c8491-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8491-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8491-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="c8491-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c8491-105">Parameters</span></span>  
 `mdmr`  
 <span data-ttu-id="c8491-106">[v] Token, `mdManifestResource` který představuje prostředek, pro který chcete získat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c8491-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="c8491-107">[out] Název prostředku.</span><span class="sxs-lookup"><span data-stu-id="c8491-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c8491-108">[v] Velikost , v širokých `szName`znaků, .</span><span class="sxs-lookup"><span data-stu-id="c8491-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="c8491-109">[out] Ukazatel na počet širokých znaků skutečně `szName`vrácených v .</span><span class="sxs-lookup"><span data-stu-id="c8491-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="c8491-110">[out] Ukazatel na `mdFile` token nebo `mdAssemblyRef` token, který představuje soubor nebo sestavení, respektive, který obsahuje prostředek.</span><span class="sxs-lookup"><span data-stu-id="c8491-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="c8491-111">[out] Ukazatel na hodnotu, která určuje posun od začátku prostředku v souboru.</span><span class="sxs-lookup"><span data-stu-id="c8491-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="c8491-112">[out] Ukazatel na příznaky, které popisují metadata použitá pro prostředek.</span><span class="sxs-lookup"><span data-stu-id="c8491-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="c8491-113">Hodnota příznaky je kombinací jedné nebo více hodnot [CorManifestResourceFlags.](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="c8491-113">The flags value is a combination of one or more [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8491-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8491-114">Requirements</span></span>  
 <span data-ttu-id="c8491-115">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8491-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8491-116">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="c8491-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c8491-117">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c8491-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c8491-118">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8491-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8491-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8491-119">See also</span></span>

- [<span data-ttu-id="c8491-120">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8491-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
