---
title: "IMetaDataEmit::SetPropertyProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetPropertyProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47bbd703c0b1d1b2038b4a6e5dc3aa677e02babe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="9220b-102">IMetaDataEmit::SetPropertyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="9220b-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="9220b-103">Nastaví uložené v metadata pro vlastnost definovanou před voláním funkce [defineproperty – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span><span class="sxs-lookup"><span data-stu-id="9220b-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9220b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9220b-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="9220b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9220b-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="9220b-106">[v] Platnost tokenu pro vlastnost, která má být změněn</span><span class="sxs-lookup"><span data-stu-id="9220b-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="9220b-107">[v] Vlastnost příznaky.</span><span class="sxs-lookup"><span data-stu-id="9220b-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="9220b-108">[v] Typ vlastnosti na výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9220b-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="9220b-109">[v] Výchozí hodnota pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9220b-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="9220b-110">[v] Počet (Unicode) znaků v `pValue`.</span><span class="sxs-lookup"><span data-stu-id="9220b-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="9220b-111">[v] Metoda, která nastavuje hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9220b-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="9220b-112">[v] Metoda, která se získá hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9220b-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="9220b-113">[v] Pole jiné metody související s vlastností.</span><span class="sxs-lookup"><span data-stu-id="9220b-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="9220b-114">Toto pole s ukončit `mdTokenNil` tokenu.</span><span class="sxs-lookup"><span data-stu-id="9220b-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9220b-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9220b-115">Requirements</span></span>  
 <span data-ttu-id="9220b-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9220b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9220b-117">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9220b-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9220b-118">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9220b-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9220b-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9220b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9220b-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="9220b-120">See Also</span></span>  
 [<span data-ttu-id="9220b-121">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9220b-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="9220b-122">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9220b-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
