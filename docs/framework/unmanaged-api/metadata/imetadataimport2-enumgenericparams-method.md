---
title: "IMetaDataImport2::EnumGenericParams – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.EnumGenericParams
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::EnumGenericParams
helpviewer_keywords:
- EnumGenericParams method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParams method [.NET Framework metadata]
ms.assetid: b50488a5-3cf0-483c-82dc-2892a3ec61ac
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0e6a5dc6cd1d82a3ccd46b09e301a84f90a3f429
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="f428f-102">IMetaDataImport2::EnumGenericParams – metoda</span><span class="sxs-lookup"><span data-stu-id="f428f-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="f428f-103">Získá enumerátor pro pole obecný parametr tokeny přidružený k zadané TypeDef nebo MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="f428f-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f428f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f428f-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,   
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],   
   [in]  ULONG            cMax,   
   [out] ULONG            *pcGenericParams  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f428f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f428f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f428f-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="f428f-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="f428f-107">[v] TypeDef nebo MethodDef token, jejichž obecné parametry mají být ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="f428f-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="f428f-108">[out] Pole Obecné parametry pro vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="f428f-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f428f-109">[v] Požadovaný maximální počet tokeny umístit `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="f428f-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="f428f-110">[out] Vrácený počet tokeny umístěných v `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="f428f-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f428f-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f428f-111">Return Value</span></span>  
  
|<span data-ttu-id="f428f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f428f-112">HRESULT</span></span>|<span data-ttu-id="f428f-113">Popis</span><span class="sxs-lookup"><span data-stu-id="f428f-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f428f-114">`EnumGenericParams`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="f428f-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f428f-115">`phEnum`nemá žádné elementy člen.</span><span class="sxs-lookup"><span data-stu-id="f428f-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="f428f-116">V takovém případě `pcGenericParams` je nastaven na hodnotu 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="f428f-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f428f-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f428f-117">Requirements</span></span>  
 <span data-ttu-id="f428f-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f428f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f428f-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f428f-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f428f-120">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f428f-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f428f-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f428f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f428f-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="f428f-122">See Also</span></span>  
 [<span data-ttu-id="f428f-123">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f428f-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="f428f-124">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f428f-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
