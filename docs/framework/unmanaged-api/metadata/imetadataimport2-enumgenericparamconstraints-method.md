---
title: IMetaDataImport2::EnumGenericParamConstraints – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParamConstraints
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParamConstraints
helpviewer_keywords:
- EnumGenericParamConstraints method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParamConstraints method [.NET Framework metadata]
ms.assetid: 8a7d4e40-28fe-4e14-b801-4049880130e7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e7a51d1ddf7a5a65ce8713161c53c1c54a5d8861
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617691"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="e42f5-102">IMetaDataImport2::EnumGenericParamConstraints – metoda</span><span class="sxs-lookup"><span data-stu-id="e42f5-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="e42f5-103">Získá enumerátor pro celou řadu omezeních obecných parametrů, které jsou přidružené k obecný parametr reprezentována zadaného tokenu.</span><span class="sxs-lookup"><span data-stu-id="e42f5-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e42f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e42f5-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e42f5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e42f5-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e42f5-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="e42f5-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="e42f5-107">[in]   Token, který představuje obecný parametr, jehož omezení jsou pro provedení výčtu.</span><span class="sxs-lookup"><span data-stu-id="e42f5-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="e42f5-108">[out] Pole omezeních obecných parametrů k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="e42f5-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e42f5-109">[in]   Maximální požadovaný počet tokenů, které mají být umístěny `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="e42f5-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="e42f5-110">[out] Ukazatel na počet tokenů umístěny do `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="e42f5-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e42f5-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e42f5-111">Return Value</span></span>  
  
|<span data-ttu-id="e42f5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e42f5-112">HRESULT</span></span>|<span data-ttu-id="e42f5-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e42f5-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e42f5-114">`EnumGenericParameterConstraints` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="e42f5-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e42f5-115">`phEnum` nemá žádné elementy člena.</span><span class="sxs-lookup"><span data-stu-id="e42f5-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="e42f5-116">V takovém případě `pcGenericParameterConstraints` je nastavena na hodnotu 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="e42f5-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e42f5-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e42f5-117">Requirements</span></span>  
 <span data-ttu-id="e42f5-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e42f5-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e42f5-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e42f5-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e42f5-120">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e42f5-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e42f5-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e42f5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e42f5-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e42f5-122">See also</span></span>
- [<span data-ttu-id="e42f5-123">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e42f5-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="e42f5-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e42f5-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
