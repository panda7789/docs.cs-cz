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
ms.openlocfilehash: d1683965193801dbdee038ab06366178891fd978
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426721"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="27890-102">IMetaDataImport2::EnumGenericParamConstraints – metoda</span><span class="sxs-lookup"><span data-stu-id="27890-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="27890-103">Získá enumerátor pro pole omezení obecného parametru přidruženého k obecnému parametru reprezentovanému zadaným tokenem.</span><span class="sxs-lookup"><span data-stu-id="27890-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27890-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27890-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27890-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="27890-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="27890-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="27890-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="27890-107">pro   Token, který představuje obecný parametr, jehož omezení mají být vyčíslena.</span><span class="sxs-lookup"><span data-stu-id="27890-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="27890-108">mimo Pole omezení obecného parametru pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="27890-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="27890-109">pro   Požadovaný maximální počet tokenů, které mají být umístěny v `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="27890-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="27890-110">mimo Ukazatel na počet tokenů umístěných v `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="27890-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27890-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="27890-111">Return Value</span></span>  
  
|<span data-ttu-id="27890-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="27890-112">HRESULT</span></span>|<span data-ttu-id="27890-113">Popis</span><span class="sxs-lookup"><span data-stu-id="27890-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="27890-114">`EnumGenericParameterConstraints` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="27890-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="27890-115">`phEnum` nemá žádné prvky členů.</span><span class="sxs-lookup"><span data-stu-id="27890-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="27890-116">V tomto případě je `pcGenericParameterConstraints` nastaveno na hodnotu 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="27890-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="27890-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="27890-117">Requirements</span></span>  
 <span data-ttu-id="27890-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27890-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27890-119">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="27890-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="27890-120">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="27890-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="27890-121">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27890-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27890-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27890-122">See also</span></span>

- [<span data-ttu-id="27890-123">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="27890-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="27890-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="27890-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
