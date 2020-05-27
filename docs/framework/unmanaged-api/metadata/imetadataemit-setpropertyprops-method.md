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
ms.openlocfilehash: b5af877c26c20bf64a27618bf24a7bce5b410419
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007777"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="0740c-102">IMetaDataEmit::SetPropertyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="0740c-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="0740c-103">Nastaví funkce uložené v metadatech pro vlastnost definovanou předchozím voláním [metody defineProperty –](imetadataemit-defineproperty-method.md).</span><span class="sxs-lookup"><span data-stu-id="0740c-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0740c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0740c-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="0740c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0740c-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="0740c-106">pro Token pro vlastnost, která má být změněna</span><span class="sxs-lookup"><span data-stu-id="0740c-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="0740c-107">pro Příznaky vlastností.</span><span class="sxs-lookup"><span data-stu-id="0740c-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="0740c-108">pro Typ výchozí hodnoty vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0740c-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="0740c-109">pro Výchozí hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0740c-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="0740c-110">pro Počet znaků (Unicode) v `pValue` .</span><span class="sxs-lookup"><span data-stu-id="0740c-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="0740c-111">pro Metoda, která nastaví hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0740c-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="0740c-112">pro Metoda, která získá hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0740c-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="0740c-113">pro Pole dalších metod přidružených k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0740c-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="0740c-114">Ukončí toto pole s `mdTokenNil` tokenem.</span><span class="sxs-lookup"><span data-stu-id="0740c-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0740c-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0740c-115">Requirements</span></span>  
 <span data-ttu-id="0740c-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0740c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0740c-117">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0740c-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0740c-118">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="0740c-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0740c-119">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0740c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0740c-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="0740c-120">See also</span></span>

- [<span data-ttu-id="0740c-121">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0740c-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="0740c-122">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0740c-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
