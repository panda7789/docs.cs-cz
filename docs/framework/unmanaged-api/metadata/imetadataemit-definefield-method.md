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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 057bae1d702fa091ebc3d3178c9fba35d5dd3d90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777653"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="792b0-102">IMetaDataEmit::DefineField – metoda</span><span class="sxs-lookup"><span data-stu-id="792b0-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="792b0-103">Vytvoří definici pro pole s podpisem Zadaná metadata a získá token pro tuto definici pole.</span><span class="sxs-lookup"><span data-stu-id="792b0-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="792b0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="792b0-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="792b0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="792b0-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="792b0-106">[in] `mdTypeDef` Token pro nadřazené třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="792b0-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="792b0-107">[in] Název pole v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="792b0-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="792b0-108">[in] Atributy pole.</span><span class="sxs-lookup"><span data-stu-id="792b0-108">[in] The field attributes.</span></span> <span data-ttu-id="792b0-109">To je bitová maska z `CorFieldAttr` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="792b0-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="792b0-110">[in] Podpis pole jako objekt BLOB.</span><span class="sxs-lookup"><span data-stu-id="792b0-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="792b0-111">[in] Počet bajtů v `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="792b0-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="792b0-112">[in] `ELEMENT_TYPE_` *\** Pro konstantní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="792b0-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="792b0-113">Jedná se `CorElementType` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="792b0-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="792b0-114">Pokud definujete není konstantní hodnotu pro pole, použijte `ELEMENT_TYPE_END`.</span><span class="sxs-lookup"><span data-stu-id="792b0-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="792b0-115">[in] Konstantní hodnoty pro pole.</span><span class="sxs-lookup"><span data-stu-id="792b0-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="792b0-116">[in] Velikost v znaky (Unicode) `pValue`.</span><span class="sxs-lookup"><span data-stu-id="792b0-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="792b0-117">[out] `mdFieldDef` Token přiřazený.</span><span class="sxs-lookup"><span data-stu-id="792b0-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="792b0-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="792b0-118">Requirements</span></span>  
 <span data-ttu-id="792b0-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="792b0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="792b0-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="792b0-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="792b0-121">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="792b0-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="792b0-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="792b0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="792b0-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="792b0-123">See also</span></span>

- [<span data-ttu-id="792b0-124">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="792b0-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="792b0-125">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="792b0-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
