---
title: IMetaDataEmit::DefineParam – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
ms.openlocfilehash: 2807458549db02598ba05f2aa80fa6ea6fbc5a13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177696"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="cf91d-102">IMetaDataEmit::DefineParam – metoda</span><span class="sxs-lookup"><span data-stu-id="cf91d-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="cf91d-103">Vytvoří definici parametru se zadaným podpisem pro metodu, na kterou odkazuje zadaný token, a získá token pro tuto definici parametru.</span><span class="sxs-lookup"><span data-stu-id="cf91d-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf91d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf91d-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineParam (  
    [in]  mdMethodDef md,
    [in]  ULONG       ulParamSeq,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,
    [out] mdParamDef  *ppd
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf91d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cf91d-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="cf91d-106">[v] Token pro metodu, jejíž parametr je definován.</span><span class="sxs-lookup"><span data-stu-id="cf91d-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="cf91d-107">[v] Pořadové číslo parametru.</span><span class="sxs-lookup"><span data-stu-id="cf91d-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="cf91d-108">[v] Název parametru v unicode.</span><span class="sxs-lookup"><span data-stu-id="cf91d-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="cf91d-109">[v] Příznaky parametru.</span><span class="sxs-lookup"><span data-stu-id="cf91d-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="cf91d-110">Toto je bitová maska `CorParamAttr` hodnot.</span><span class="sxs-lookup"><span data-stu-id="cf91d-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="cf91d-111">[v] `ELEMENT_TYPE_` pro konstantní hodnotu. *\**</span><span class="sxs-lookup"><span data-stu-id="cf91d-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="cf91d-112">[v] Konstantní hodnota parametru.</span><span class="sxs-lookup"><span data-stu-id="cf91d-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="cf91d-113">[v] Velikost znaku Unicode . `pValue`</span><span class="sxs-lookup"><span data-stu-id="cf91d-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="cf91d-114">[out] Přiřazen `mdParamDef` token.</span><span class="sxs-lookup"><span data-stu-id="cf91d-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf91d-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cf91d-115">Remarks</span></span>  
 <span data-ttu-id="cf91d-116">Sekvenční `ulParamSeq` hodnoty v začíná 1 pro parametry.</span><span class="sxs-lookup"><span data-stu-id="cf91d-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="cf91d-117">Vrácená hodnota má pořadové číslo 0.</span><span class="sxs-lookup"><span data-stu-id="cf91d-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf91d-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cf91d-118">Requirements</span></span>  
 <span data-ttu-id="cf91d-119">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf91d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf91d-120">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="cf91d-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cf91d-121">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf91d-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf91d-122">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf91d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf91d-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf91d-123">See also</span></span>

- [<span data-ttu-id="cf91d-124">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf91d-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="cf91d-125">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf91d-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
