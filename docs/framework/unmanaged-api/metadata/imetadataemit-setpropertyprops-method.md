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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 024ab8254f566e5386198fa1735af4c6b1972ca1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448033"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="20dd0-102">IMetaDataEmit::SetPropertyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="20dd0-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="20dd0-103">Nastaví uložené v metadata pro vlastnost definovanou před voláním funkce [defineproperty – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span><span class="sxs-lookup"><span data-stu-id="20dd0-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20dd0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20dd0-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="20dd0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="20dd0-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="20dd0-106">[v] Platnost tokenu pro vlastnost, která má být změněn</span><span class="sxs-lookup"><span data-stu-id="20dd0-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="20dd0-107">[v] Vlastnost příznaky.</span><span class="sxs-lookup"><span data-stu-id="20dd0-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="20dd0-108">[v] Typ vlastnosti na výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="20dd0-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="20dd0-109">[v] Výchozí hodnota pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="20dd0-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="20dd0-110">[v] Počet (Unicode) znaků v `pValue`.</span><span class="sxs-lookup"><span data-stu-id="20dd0-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="20dd0-111">[v] Metoda, která nastavuje hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="20dd0-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="20dd0-112">[v] Metoda, která se získá hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="20dd0-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="20dd0-113">[v] Pole jiné metody související s vlastností.</span><span class="sxs-lookup"><span data-stu-id="20dd0-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="20dd0-114">Toto pole s ukončit `mdTokenNil` tokenu.</span><span class="sxs-lookup"><span data-stu-id="20dd0-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20dd0-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20dd0-115">Requirements</span></span>  
 <span data-ttu-id="20dd0-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20dd0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20dd0-117">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="20dd0-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="20dd0-118">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="20dd0-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20dd0-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20dd0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20dd0-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="20dd0-120">See Also</span></span>  
 [<span data-ttu-id="20dd0-121">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20dd0-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="20dd0-122">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20dd0-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
