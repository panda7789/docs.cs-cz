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
ms.openlocfilehash: 1868d13a9dbb73dbdf64e49c395bdbff02ce89d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177443"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="16615-102">IMetaDataEmit2::DefineGenericParam – metoda</span><span class="sxs-lookup"><span data-stu-id="16615-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="16615-103">Vytvoří definici parametru obecného typu a získá token pro tento parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="16615-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16615-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16615-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="16615-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="16615-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="16615-106">[v] Nebo `mdTypeDef` `mdMethodDef` token, který představuje metodu nebo konstruktor, pro který chcete definovat obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="16615-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="16615-107">[v] Index obecného parametru.</span><span class="sxs-lookup"><span data-stu-id="16615-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="16615-108">[v] Hodnota [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) výčtu, který popisuje typ pro obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="16615-108">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="16615-109">[v] Název parametru.</span><span class="sxs-lookup"><span data-stu-id="16615-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="16615-110">[v] Tento parametr je vyhrazen pro budoucí rozšiřitelnost.</span><span class="sxs-lookup"><span data-stu-id="16615-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="16615-111">[v] Pole typu s nulovým ukončem.</span><span class="sxs-lookup"><span data-stu-id="16615-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="16615-112">Členové pole musí `mdTypeDef` `mdTypeRef`být `mdTypeSpec` token , nebo metadat.</span><span class="sxs-lookup"><span data-stu-id="16615-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="16615-113">[out] Token, který představuje obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="16615-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16615-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="16615-114">Requirements</span></span>  
 <span data-ttu-id="16615-115">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16615-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16615-116">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="16615-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="16615-117">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="16615-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="16615-118">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16615-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16615-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="16615-119">See also</span></span>

- [<span data-ttu-id="16615-120">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="16615-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="16615-121">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="16615-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
