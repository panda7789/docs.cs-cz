---
title: IMetaDataImport2::GetGenericParamProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9ded6b4e0ac8f3e70fd0145ab6e2410c3b38e02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448671"
---
# <a name="imetadataimport2getgenericparamprops-method"></a><span data-ttu-id="8c97c-102">IMetaDataImport2::GetGenericParamProps – metoda</span><span class="sxs-lookup"><span data-stu-id="8c97c-102">IMetaDataImport2::GetGenericParamProps Method</span></span>
<span data-ttu-id="8c97c-103">Získá metadata přidružená obecný parametr reprezentována zadaný token.</span><span class="sxs-lookup"><span data-stu-id="8c97c-103">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c97c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c97c-104">Syntax</span></span>  
  
```  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c97c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c97c-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="8c97c-106">[v] Token, který reprezentuje obecný parametr, pro které chcete vrátit metadata.</span><span class="sxs-lookup"><span data-stu-id="8c97c-106">[in] The token that represents the generic parameter for which to return metadata.</span></span>  
  
 `pulParamSeq`  
 <span data-ttu-id="8c97c-107">[out] Pořadová čísla `Type` parametr konstruktoru nadřazené nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="8c97c-107">[out] The ordinal position of the `Type` parameter in the parent constructor or method.</span></span>  
  
 `pdwParamFlags`  
 <span data-ttu-id="8c97c-108">[out] Hodnota [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) výčet, který popisuje `Type` pro obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="8c97c-108">[out] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the `Type` for the generic parameter.</span></span>  
  
 `ptOwner`  
 <span data-ttu-id="8c97c-109">[out] TypeDef nebo MethodDef token, který představuje vlastník parametru.</span><span class="sxs-lookup"><span data-stu-id="8c97c-109">[out] A TypeDef or MethodDef token that represents the owner of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="8c97c-110">[out] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="8c97c-110">[out] Reserved for future extensibility.</span></span>  
  
 `wzName`  
 <span data-ttu-id="8c97c-111">[out] Název obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="8c97c-111">[out] The name of the generic parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="8c97c-112">[v] Velikost `wzName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="8c97c-112">[in] The size of the `wzName` buffer.</span></span>  
  
 `pchName`  
 <span data-ttu-id="8c97c-113">[out] Vrácený velikost názvu v široké znaky.</span><span class="sxs-lookup"><span data-stu-id="8c97c-113">[out] The returned size of the name, in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c97c-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c97c-114">Requirements</span></span>  
 <span data-ttu-id="8c97c-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c97c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c97c-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8c97c-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8c97c-117">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8c97c-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8c97c-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c97c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c97c-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c97c-119">See Also</span></span>  
 [<span data-ttu-id="8c97c-120">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c97c-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="8c97c-121">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c97c-121">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
