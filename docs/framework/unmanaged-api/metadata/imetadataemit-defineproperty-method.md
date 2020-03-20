---
title: IMetaDataEmit::DefineProperty – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineProperty
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type:
- apiref
ms.openlocfilehash: eb3ecbf39376e7126b5ec93a26badcbf5076d1db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175782"
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="d6e58-102">IMetaDataEmit::DefineProperty – metoda</span><span class="sxs-lookup"><span data-stu-id="d6e58-102">IMetaDataEmit::DefineProperty Method</span></span>
<span data-ttu-id="d6e58-103">Vytvoří definici vlastnosti pro zadaný `get` `set` typ se zadanými přístupovými objekty a přistupujícími objekty metody a získá token pro tuto definici vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d6e58-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6e58-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6e58-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineProperty (
    [in]  mdTypeDef          td,
    [in]  LPCWSTR            szProperty,
    [in]  DWORD              dwPropFlags,
    [in]  PCCOR_SIGNATURE    pvSig,
    [in]  ULONG              cbSig,
    [in]  DWORD              dwCPlusTypeFlag,
    [in]  void const         *pValue,
    [in]  ULONG              cchValue,
    [in]  mdMethodDef        mdSetter,
    [in]  mdMethodDef        mdGetter,
    [in]  mdMethodDef        rmdOtherMethods[],
    [out] mdProperty         *pmdProp
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6e58-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6e58-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="d6e58-106">[v] Token pro třídu nebo rozhraní, na kterém je definována vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d6e58-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="d6e58-107">[v] Název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d6e58-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="d6e58-108">[v] Příznaky vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d6e58-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="d6e58-109">[v] Podpis vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d6e58-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="d6e58-110">[v] Počet bajtů v `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="d6e58-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="d6e58-111">[v] Typ výchozí hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d6e58-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="d6e58-112">[v] Výchozí hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d6e58-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="d6e58-113">[v] Počet znaků (Unicode) `pValue`v .</span><span class="sxs-lookup"><span data-stu-id="d6e58-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="d6e58-114">[v] Metoda, která nastaví hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d6e58-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="d6e58-115">[v] Metoda, která získá hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d6e58-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="d6e58-116">[v] Pole dalších metod spojených s vlastností.</span><span class="sxs-lookup"><span data-stu-id="d6e58-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="d6e58-117">Ukončete `mdTokenNil`pole pomocí .</span><span class="sxs-lookup"><span data-stu-id="d6e58-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="d6e58-118">[out] Přiřazen `mdProperty` token.</span><span class="sxs-lookup"><span data-stu-id="d6e58-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6e58-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6e58-119">Requirements</span></span>  
 <span data-ttu-id="d6e58-120">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6e58-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6e58-121">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="d6e58-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6e58-122">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d6e58-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6e58-123">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6e58-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6e58-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6e58-124">See also</span></span>

- [<span data-ttu-id="d6e58-125">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6e58-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d6e58-126">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6e58-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
