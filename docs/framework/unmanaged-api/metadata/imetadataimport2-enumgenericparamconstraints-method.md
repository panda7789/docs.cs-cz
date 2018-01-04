---
title: "IMetaDataImport2::EnumGenericParamConstraints – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.EnumGenericParamConstraints
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::EnumGenericParamConstraints
helpviewer_keywords:
- EnumGenericParamConstraints method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParamConstraints method [.NET Framework metadata]
ms.assetid: 8a7d4e40-28fe-4e14-b801-4049880130e7
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72f863205c0fa7f4c6b4477c9d9143d1923a5d4c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="2f3bd-102">IMetaDataImport2::EnumGenericParamConstraints – metoda</span><span class="sxs-lookup"><span data-stu-id="2f3bd-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="2f3bd-103">Získá enumerátor pro pole obecný parametr omezení spojené s obecný parametr reprezentována zadaný token.</span><span class="sxs-lookup"><span data-stu-id="2f3bd-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f3bd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f3bd-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2f3bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f3bd-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="2f3bd-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="2f3bd-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="2f3bd-107">[v]   Token, který reprezentuje obecný parametr, jehož omezení mají být ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="2f3bd-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="2f3bd-108">[out] Pole omezení obecný parametr k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="2f3bd-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2f3bd-109">[v]   Požadovaný maximální počet tokeny umístit `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="2f3bd-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="2f3bd-110">[out] Ukazatel na počet tokeny umístit do `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="2f3bd-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f3bd-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2f3bd-111">Return Value</span></span>  
  
|<span data-ttu-id="2f3bd-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2f3bd-112">HRESULT</span></span>|<span data-ttu-id="2f3bd-113">Popis</span><span class="sxs-lookup"><span data-stu-id="2f3bd-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2f3bd-114">`EnumGenericParameterConstraints`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="2f3bd-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2f3bd-115">`phEnum`nemá žádné elementy člen.</span><span class="sxs-lookup"><span data-stu-id="2f3bd-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="2f3bd-116">V takovém případě `pcGenericParameterConstraints` je nastaven na hodnotu 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="2f3bd-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2f3bd-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2f3bd-117">Requirements</span></span>  
 <span data-ttu-id="2f3bd-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f3bd-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f3bd-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2f3bd-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2f3bd-120">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2f3bd-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2f3bd-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f3bd-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f3bd-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f3bd-122">See Also</span></span>  
 [<span data-ttu-id="2f3bd-123">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f3bd-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="2f3bd-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f3bd-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
