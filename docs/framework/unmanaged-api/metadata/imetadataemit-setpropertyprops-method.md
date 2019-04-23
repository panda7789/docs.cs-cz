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
ms.openlocfilehash: fdee8491b22675fb8dd8fa89e77ebf8541185173
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207888"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="893cd-102">IMetaDataEmit::SetPropertyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="893cd-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="893cd-103">Nastaví uložená v metadatech pro vlastnosti určené předchozím volání funkce [DefineProperty – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span><span class="sxs-lookup"><span data-stu-id="893cd-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="893cd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="893cd-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="893cd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="893cd-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="893cd-106">[in] Token pro vlastnost, která má být změněn</span><span class="sxs-lookup"><span data-stu-id="893cd-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="893cd-107">[in] Vlastnost příznaky.</span><span class="sxs-lookup"><span data-stu-id="893cd-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="893cd-108">[in] Typ vlastnosti na výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="893cd-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="893cd-109">[in] Výchozí hodnota pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="893cd-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="893cd-110">[in] Počet (Unicode) znaky v `pValue`.</span><span class="sxs-lookup"><span data-stu-id="893cd-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="893cd-111">[in] Metoda, která nastaví hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="893cd-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="893cd-112">[in] Metoda, která vrací hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="893cd-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="893cd-113">[in] Pole jiné metody přidružený k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="893cd-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="893cd-114">Toto pole se ukončí `mdTokenNil` token.</span><span class="sxs-lookup"><span data-stu-id="893cd-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="893cd-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="893cd-115">Requirements</span></span>  
 <span data-ttu-id="893cd-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="893cd-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="893cd-117">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="893cd-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="893cd-118">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="893cd-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="893cd-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="893cd-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="893cd-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="893cd-120">See also</span></span>

- [<span data-ttu-id="893cd-121">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="893cd-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="893cd-122">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="893cd-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
