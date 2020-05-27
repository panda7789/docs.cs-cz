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
ms.openlocfilehash: 479cb25ad8e1c263d3539a4203ac5bea781eb931
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009372"
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="c3632-102">IMetaDataEmit::DefineProperty – metoda</span><span class="sxs-lookup"><span data-stu-id="c3632-102">IMetaDataEmit::DefineProperty Method</span></span>
<span data-ttu-id="c3632-103">Vytvoří definici vlastnosti pro zadaný typ se zadaným `get` a přístupovým objektem `set` metody a získá token do této definice vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c3632-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3632-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3632-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c3632-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3632-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="c3632-106">pro Token třídy nebo rozhraní, na kterém je vlastnost definována.</span><span class="sxs-lookup"><span data-stu-id="c3632-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="c3632-107">pro Název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c3632-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="c3632-108">pro Příznaky vlastností.</span><span class="sxs-lookup"><span data-stu-id="c3632-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="c3632-109">pro Signatura vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c3632-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="c3632-110">pro Počet bajtů v `pvSig` .</span><span class="sxs-lookup"><span data-stu-id="c3632-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="c3632-111">pro Typ výchozí hodnoty vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c3632-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="c3632-112">pro Výchozí hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c3632-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="c3632-113">pro Počet znaků (Unicode) v `pValue` .</span><span class="sxs-lookup"><span data-stu-id="c3632-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="c3632-114">pro Metoda, která nastaví hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c3632-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="c3632-115">pro Metoda, která získá hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c3632-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="c3632-116">pro Pole dalších metod přidružených k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c3632-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="c3632-117">Ukončete pole pomocí `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="c3632-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="c3632-118">mimo `mdProperty`Přiřazený token.</span><span class="sxs-lookup"><span data-stu-id="c3632-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3632-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c3632-119">Requirements</span></span>  
 <span data-ttu-id="c3632-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3632-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3632-121">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c3632-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c3632-122">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="c3632-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3632-123">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3632-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3632-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3632-124">See also</span></span>

- [<span data-ttu-id="c3632-125">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3632-125">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="c3632-126">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3632-126">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
