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
ms.openlocfilehash: f66b0145dbaece7292d2ccad169a97fbb10b6d11
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186677"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="f816d-102">IMetaDataImport2::EnumGenericParamConstraints – metoda</span><span class="sxs-lookup"><span data-stu-id="f816d-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="f816d-103">Získá enumerátor pro celou řadu omezeních obecných parametrů, které jsou přidružené k obecný parametr reprezentována zadaného tokenu.</span><span class="sxs-lookup"><span data-stu-id="f816d-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f816d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f816d-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f816d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f816d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f816d-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="f816d-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="f816d-107">[in]   Token, který představuje obecný parametr, jehož omezení jsou pro provedení výčtu.</span><span class="sxs-lookup"><span data-stu-id="f816d-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="f816d-108">[out] Pole omezeních obecných parametrů k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="f816d-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f816d-109">[in]   Maximální požadovaný počet tokenů, které mají být umístěny `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="f816d-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="f816d-110">[out] Ukazatel na počet tokenů umístěny do `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="f816d-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f816d-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f816d-111">Return Value</span></span>  
  
|<span data-ttu-id="f816d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f816d-112">HRESULT</span></span>|<span data-ttu-id="f816d-113">Popis</span><span class="sxs-lookup"><span data-stu-id="f816d-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumGenericParameterConstraints` <span data-ttu-id="f816d-114">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="f816d-114">returned successfully.</span></span>|  
|`S_FALSE`|`phEnum` <span data-ttu-id="f816d-115">nemá žádné elementy člena.</span><span class="sxs-lookup"><span data-stu-id="f816d-115">has no member elements.</span></span> <span data-ttu-id="f816d-116">V takovém případě `pcGenericParameterConstraints` je nastavena na hodnotu 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="f816d-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f816d-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f816d-117">Requirements</span></span>  
 <span data-ttu-id="f816d-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f816d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f816d-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f816d-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f816d-120">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f816d-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="f816d-121">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f816d-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f816d-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f816d-122">See also</span></span>

- [<span data-ttu-id="f816d-123">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f816d-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="f816d-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f816d-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
