---
title: IMetaDataImport2::EnumGenericParams – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParams
helpviewer_keywords:
- EnumGenericParams method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParams method [.NET Framework metadata]
ms.assetid: b50488a5-3cf0-483c-82dc-2892a3ec61ac
topic_type:
- apiref
ms.openlocfilehash: 55709e79cd8bdb36fe1e32ee8a699fccb1b1bbc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175301"
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="cd4da-102">IMetaDataImport2::EnumGenericParams – metoda</span><span class="sxs-lookup"><span data-stu-id="cd4da-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="cd4da-103">Získá čítač pro pole tokenů obecných parametrů přidružených k zadanému tokenu TypeDef nebo MethodDef.</span><span class="sxs-lookup"><span data-stu-id="cd4da-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd4da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd4da-104">Syntax</span></span>  
  
```cpp
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],
   [in]  ULONG            cMax,
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd4da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd4da-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="cd4da-106">[dovnitř, ven] Ukazatel na čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="cd4da-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="cd4da-107">[v] Token TypeDef nebo MethodDef, jehož obecné parametry mají být uvedeny.</span><span class="sxs-lookup"><span data-stu-id="cd4da-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="cd4da-108">[out] Pole obecných parametrů pro výčet.</span><span class="sxs-lookup"><span data-stu-id="cd4da-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="cd4da-109">[v] Požadovaný maximální počet tokenů, `rGenericParams`které mají být umístit v .</span><span class="sxs-lookup"><span data-stu-id="cd4da-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="cd4da-110">[out] Vrácený počet tokenů `rGenericParams`umístěných v .</span><span class="sxs-lookup"><span data-stu-id="cd4da-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd4da-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cd4da-111">Return Value</span></span>  
  
|<span data-ttu-id="cd4da-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cd4da-112">HRESULT</span></span>|<span data-ttu-id="cd4da-113">Popis</span><span class="sxs-lookup"><span data-stu-id="cd4da-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="cd4da-114">`EnumGenericParams`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="cd4da-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="cd4da-115">`phEnum`nemá žádné členské prvky.</span><span class="sxs-lookup"><span data-stu-id="cd4da-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="cd4da-116">V tomto `pcGenericParams` případě je nastavena na 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="cd4da-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd4da-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cd4da-117">Requirements</span></span>  
 <span data-ttu-id="cd4da-118">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd4da-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd4da-119">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="cd4da-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cd4da-120">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cd4da-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cd4da-121">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd4da-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd4da-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd4da-122">See also</span></span>

- [<span data-ttu-id="cd4da-123">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cd4da-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="cd4da-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cd4da-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
