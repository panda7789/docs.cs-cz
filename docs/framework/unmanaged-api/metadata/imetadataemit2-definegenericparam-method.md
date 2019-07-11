---
title: IMetaDataEmit2::DefineGenericParam – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineGenericParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 027547098edefdca71317b8f885e71f468dc6e77
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777197"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="d7d06-102">IMetaDataEmit2::DefineGenericParam – metoda</span><span class="sxs-lookup"><span data-stu-id="d7d06-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="d7d06-103">Vytvoří definici pro parametr obecného typu a získá token pro tento parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d7d06-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7d06-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7d06-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="d7d06-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7d06-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="d7d06-106">[in] `mdTypeDef` Nebo `mdMethodDef` token, který představuje tato metoda nebo konstruktor, pro které chcete definovat obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="d7d06-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="d7d06-107">[in] Index obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="d7d06-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="d7d06-108">[in] Hodnota [corgenericparamattr –](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) výčet, který popisuje typu pro obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="d7d06-108">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="d7d06-109">[in] Název parametru.</span><span class="sxs-lookup"><span data-stu-id="d7d06-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="d7d06-110">[in] Tento parametr je vyhrazený pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="d7d06-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="d7d06-111">[in] Ukončit nulou pole omezení typu.</span><span class="sxs-lookup"><span data-stu-id="d7d06-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="d7d06-112">Členy pole musí být `mdTypeDef`, `mdTypeRef`, nebo `mdTypeSpec` token metadat.</span><span class="sxs-lookup"><span data-stu-id="d7d06-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="d7d06-113">[out] Token, který představuje obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="d7d06-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7d06-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d7d06-114">Requirements</span></span>  
 <span data-ttu-id="d7d06-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7d06-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7d06-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d7d06-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d7d06-117">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d7d06-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d7d06-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7d06-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7d06-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d7d06-119">See also</span></span>

- [<span data-ttu-id="d7d06-120">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d7d06-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="d7d06-121">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d7d06-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
