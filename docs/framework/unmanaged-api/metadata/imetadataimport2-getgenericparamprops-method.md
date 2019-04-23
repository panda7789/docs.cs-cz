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
ms.openlocfilehash: 55a765fe3942cbf71a8460187e829dc7f3ca877e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59082331"
---
# <a name="imetadataimport2getgenericparamprops-method"></a><span data-ttu-id="b1856-102">IMetaDataImport2::GetGenericParamProps – metoda</span><span class="sxs-lookup"><span data-stu-id="b1856-102">IMetaDataImport2::GetGenericParamProps Method</span></span>
<span data-ttu-id="b1856-103">Získá metadata přidružená k obecný parametr reprezentována zadaného tokenu.</span><span class="sxs-lookup"><span data-stu-id="b1856-103">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1856-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1856-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b1856-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1856-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="b1856-106">[in] Token, který představuje obecný parametr, pro které se mají vrátit metadata.</span><span class="sxs-lookup"><span data-stu-id="b1856-106">[in] The token that represents the generic parameter for which to return metadata.</span></span>  
  
 `pulParamSeq`  
 <span data-ttu-id="b1856-107">[out] Pořadové číslo pozice `Type` parametr v konstruktoru nadřazené nebo metody.</span><span class="sxs-lookup"><span data-stu-id="b1856-107">[out] The ordinal position of the `Type` parameter in the parent constructor or method.</span></span>  
  
 `pdwParamFlags`  
 <span data-ttu-id="b1856-108">[out] Hodnota [corgenericparamattr –](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) výčet, který popisuje `Type` pro obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="b1856-108">[out] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the `Type` for the generic parameter.</span></span>  
  
 `ptOwner`  
 <span data-ttu-id="b1856-109">[out] Token TypeDef nebo MethodDef, který představuje vlastníka parametru.</span><span class="sxs-lookup"><span data-stu-id="b1856-109">[out] A TypeDef or MethodDef token that represents the owner of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="b1856-110">[out] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="b1856-110">[out] Reserved for future extensibility.</span></span>  
  
 `wzName`  
 <span data-ttu-id="b1856-111">[out] Název obecného parametru.</span><span class="sxs-lookup"><span data-stu-id="b1856-111">[out] The name of the generic parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b1856-112">[in] Velikost `wzName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="b1856-112">[in] The size of the `wzName` buffer.</span></span>  
  
 `pchName`  
 <span data-ttu-id="b1856-113">[out] Vrácená velikost názvu v širokých znaků.</span><span class="sxs-lookup"><span data-stu-id="b1856-113">[out] The returned size of the name, in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1856-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1856-114">Requirements</span></span>  
 <span data-ttu-id="b1856-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1856-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1856-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b1856-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b1856-117">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b1856-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b1856-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1856-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1856-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1856-119">See also</span></span>

- [<span data-ttu-id="b1856-120">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b1856-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="b1856-121">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b1856-121">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
