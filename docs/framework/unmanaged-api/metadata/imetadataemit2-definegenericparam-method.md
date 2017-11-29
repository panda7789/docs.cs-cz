---
title: "IMetaDataEmit2::DefineGenericParam – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.DefineGenericParam
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 737e57b86e74cc7e4668589d16c2e2cb351162bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="d83c8-102">IMetaDataEmit2::DefineGenericParam – metoda</span><span class="sxs-lookup"><span data-stu-id="d83c8-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="d83c8-103">Vytvoří definici pro parametr obecného typu a získá token pro tento parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d83c8-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d83c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d83c8-104">Syntax</span></span>  
  
```  
HRESULT DefineGenericParam (   
    [in]  mdToken         tk,   
    [in]  ULONG           ulParamSeq,   
    [in]  DWORD           dwParamFlags,   
    [in]  LPCWSTR         szname,   
    [in]  DWORD           reserved,   
    [in]  mdToken         rtkConstraints[],   
    [out] mdGenericParam  *pgp  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d83c8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d83c8-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="d83c8-106">[v] `mdTypeDef` Nebo `mdMethodDef` token, který představuje metoda nebo konstruktor, pro které chcete definovat obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="d83c8-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="d83c8-107">[v] Index obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="d83c8-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="d83c8-108">[v] Hodnota [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) výčet, který popisuje typ pro obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="d83c8-108">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="d83c8-109">[v] Název parametru.</span><span class="sxs-lookup"><span data-stu-id="d83c8-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="d83c8-110">[v] Tento parametr je vyhrazená pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="d83c8-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="d83c8-111">[v] Byl ukončen nula pole Typ omezení.</span><span class="sxs-lookup"><span data-stu-id="d83c8-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="d83c8-112">Pole členů musí být `mdTypeDef`, `mdTypeRef`, nebo `mdTypeSpec` metadata token.</span><span class="sxs-lookup"><span data-stu-id="d83c8-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="d83c8-113">[out] Token, který reprezentuje obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="d83c8-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d83c8-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d83c8-114">Requirements</span></span>  
 <span data-ttu-id="d83c8-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d83c8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d83c8-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d83c8-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d83c8-117">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d83c8-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d83c8-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d83c8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d83c8-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="d83c8-119">See Also</span></span>  
 [<span data-ttu-id="d83c8-120">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d83c8-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="d83c8-121">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d83c8-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
