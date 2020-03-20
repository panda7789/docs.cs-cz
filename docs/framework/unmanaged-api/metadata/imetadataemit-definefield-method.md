---
title: IMetaDataEmit::DefineField – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
ms.openlocfilehash: 8ca5ab70f60de4d783800fb18612a8f04cb9cee1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177705"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="2b50f-102">IMetaDataEmit::DefineField – metoda</span><span class="sxs-lookup"><span data-stu-id="2b50f-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="2b50f-103">Vytvoří definici pole se zadaným podpisem metadat a získá token pro tuto definici pole.</span><span class="sxs-lookup"><span data-stu-id="2b50f-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b50f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b50f-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineField (
    [in]  mdTypeDef   td,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwFieldFlags,
    [in]  PCCOR_SIGNATURE pvSigBlob,
    [in]  ULONG       cbSigBlob,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue,
    [out] mdFieldDef  *pmd
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b50f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b50f-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="2b50f-106">[v] Token `mdTypeDef` pro ohraničující třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2b50f-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="2b50f-107">[v] Název pole v unicode.</span><span class="sxs-lookup"><span data-stu-id="2b50f-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="2b50f-108">[v] Atributy pole.</span><span class="sxs-lookup"><span data-stu-id="2b50f-108">[in] The field attributes.</span></span> <span data-ttu-id="2b50f-109">Toto je bitová maska `CorFieldAttr` hodnot.</span><span class="sxs-lookup"><span data-stu-id="2b50f-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="2b50f-110">[v] Podpis pole jako objekt BLOB.</span><span class="sxs-lookup"><span data-stu-id="2b50f-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="2b50f-111">[v] Počet bajtů v `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="2b50f-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="2b50f-112">[v] Pro `ELEMENT_TYPE_` *\** konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2b50f-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="2b50f-113">To je `CorElementType` hodnota.</span><span class="sxs-lookup"><span data-stu-id="2b50f-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="2b50f-114">Pokud nedefinujete konstantní hodnotu pole, použijte `ELEMENT_TYPE_END`.</span><span class="sxs-lookup"><span data-stu-id="2b50f-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="2b50f-115">[v] Konstantní hodnota pole.</span><span class="sxs-lookup"><span data-stu-id="2b50f-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="2b50f-116">[v] Velikost znaků (Unicode) `pValue`.</span><span class="sxs-lookup"><span data-stu-id="2b50f-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="2b50f-117">[out] Přiřazen `mdFieldDef` token.</span><span class="sxs-lookup"><span data-stu-id="2b50f-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b50f-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2b50f-118">Requirements</span></span>  
 <span data-ttu-id="2b50f-119">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b50f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b50f-120">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="2b50f-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2b50f-121">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2b50f-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2b50f-122">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b50f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b50f-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="2b50f-123">See also</span></span>

- [<span data-ttu-id="2b50f-124">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b50f-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="2b50f-125">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b50f-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
