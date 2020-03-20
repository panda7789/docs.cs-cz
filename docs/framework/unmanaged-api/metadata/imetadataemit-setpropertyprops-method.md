---
title: IMetaDataEmit::SetPropertyProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type:
- apiref
ms.openlocfilehash: dc6375f3e2cff1a744a8ff2e6a6adab27bbf8af3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177479"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="13d88-102">IMetaDataEmit::SetPropertyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="13d88-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="13d88-103">Nastaví funkce uložené v metadatech pro vlastnost definovanou předchozím voláním [metody DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span><span class="sxs-lookup"><span data-stu-id="13d88-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13d88-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13d88-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPropertyProps (
    [in]  mdProperty      pr,
    [in]  DWORD           dwPropFlags,
    [in]  DWORD           dwCPlusTypeFlag,
    [in]  void const      *pValue,
    [in]  ULONG           cchValue,
    [in]  mdMethodDef     mdSetter,
    [in]  mdMethodDef     mdGetter,
    [in]  mdMethodDef     rmdOtherMethods[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13d88-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="13d88-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="13d88-106">[v] Token pro vlastnost, která má být změněna</span><span class="sxs-lookup"><span data-stu-id="13d88-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="13d88-107">[v] Příznaky vlastností.</span><span class="sxs-lookup"><span data-stu-id="13d88-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="13d88-108">[v] Typ výchozí hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="13d88-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="13d88-109">[v] Výchozí hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="13d88-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="13d88-110">[v] Počet znaků (Unicode) `pValue`v .</span><span class="sxs-lookup"><span data-stu-id="13d88-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="13d88-111">[v] Metoda, která nastaví hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="13d88-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="13d88-112">[v] Metoda, která získá hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="13d88-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="13d88-113">[v] Pole dalších metod spojených s vlastností.</span><span class="sxs-lookup"><span data-stu-id="13d88-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="13d88-114">Ukončete `mdTokenNil` toto pole tokenem.</span><span class="sxs-lookup"><span data-stu-id="13d88-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13d88-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="13d88-115">Requirements</span></span>  
 <span data-ttu-id="13d88-116">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13d88-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13d88-117">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="13d88-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="13d88-118">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="13d88-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13d88-119">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13d88-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13d88-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="13d88-120">See also</span></span>

- [<span data-ttu-id="13d88-121">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="13d88-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="13d88-122">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="13d88-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
