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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ecd1c714f41c76833ef6a0a4b7be87e338ca1a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448827"
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="0d707-102">IMetaDataImport2::EnumGenericParams – metoda</span><span class="sxs-lookup"><span data-stu-id="0d707-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="0d707-103">Získá enumerátor pro pole obecný parametr tokeny přidružený k zadané TypeDef nebo MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="0d707-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d707-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d707-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,   
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],   
   [in]  ULONG            cMax,   
   [out] ULONG            *pcGenericParams  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0d707-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0d707-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="0d707-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="0d707-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="0d707-107">[v] TypeDef nebo MethodDef token, jejichž obecné parametry mají být ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="0d707-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="0d707-108">[out] Pole Obecné parametry pro vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="0d707-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0d707-109">[v] Požadovaný maximální počet tokeny umístit `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="0d707-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="0d707-110">[out] Vrácený počet tokeny umístěných v `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="0d707-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d707-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0d707-111">Return Value</span></span>  
  
|<span data-ttu-id="0d707-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0d707-112">HRESULT</span></span>|<span data-ttu-id="0d707-113">Popis</span><span class="sxs-lookup"><span data-stu-id="0d707-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="0d707-114">`EnumGenericParams` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="0d707-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="0d707-115">`phEnum` nemá žádné elementy člen.</span><span class="sxs-lookup"><span data-stu-id="0d707-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="0d707-116">V takovém případě `pcGenericParams` je nastaven na hodnotu 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="0d707-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0d707-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0d707-117">Requirements</span></span>  
 <span data-ttu-id="0d707-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d707-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d707-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0d707-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0d707-120">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0d707-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0d707-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d707-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d707-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d707-122">See Also</span></span>  
 [<span data-ttu-id="0d707-123">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0d707-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="0d707-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0d707-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
