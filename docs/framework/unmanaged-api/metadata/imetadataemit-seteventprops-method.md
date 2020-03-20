---
title: IMetaDataEmit::SetEventProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type:
- apiref
ms.openlocfilehash: f664e694303691fb1132150037dcbcdb5549539a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177532"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="6a6ad-102">IMetaDataEmit::SetEventProps – metoda</span><span class="sxs-lookup"><span data-stu-id="6a6ad-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="6a6ad-103">Nastaví nebo aktualizuje zadanou funkci události definované předchozím voláním [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="6a6ad-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a6ad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a6ad-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,
    [in]  DWORD       dwEventFlags,
    [in]  mdToken     tkEventType,
    [in]  mdMethodDef mdAddOn,
    [in]  mdMethodDef mdRemoveOn,
    [in]  mdMethodDef mdFire,
    [in]  mdMethodDef rmdOtherMethods[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a6ad-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a6ad-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="6a6ad-106">[v] Token události.</span><span class="sxs-lookup"><span data-stu-id="6a6ad-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="6a6ad-107">[v] Příznaky události.</span><span class="sxs-lookup"><span data-stu-id="6a6ad-107">[in] Event flags.</span></span> <span data-ttu-id="6a6ad-108">Toto je bitová maska `CorEventAttr` hodnot.</span><span class="sxs-lookup"><span data-stu-id="6a6ad-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="6a6ad-109">[v] Token pro třídu události.</span><span class="sxs-lookup"><span data-stu-id="6a6ad-109">[in] The token for the event class.</span></span> <span data-ttu-id="6a6ad-110">Toto je `mdTypeDef` buď `mdTypeRef` token nebo.</span><span class="sxs-lookup"><span data-stu-id="6a6ad-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="6a6ad-111">[v] Metoda použitá k přihlášení k odběru události nebo null.</span><span class="sxs-lookup"><span data-stu-id="6a6ad-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="6a6ad-112">[v] Metoda použitá k odhlášení z odběru události nebo null.</span><span class="sxs-lookup"><span data-stu-id="6a6ad-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="6a6ad-113">[v] Metoda použitá (odvozenou třídou) k navojení události.</span><span class="sxs-lookup"><span data-stu-id="6a6ad-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="6a6ad-114">[v] Pole tokenů pro jiné metody přidružené k události.</span><span class="sxs-lookup"><span data-stu-id="6a6ad-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="6a6ad-115">Poslední prvek pole musí `mdMethodDefNil`být .</span><span class="sxs-lookup"><span data-stu-id="6a6ad-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a6ad-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a6ad-116">Requirements</span></span>  
 <span data-ttu-id="6a6ad-117">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a6ad-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a6ad-118">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="6a6ad-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6a6ad-119">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6a6ad-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a6ad-120">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a6ad-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a6ad-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a6ad-121">See also</span></span>

- [<span data-ttu-id="6a6ad-122">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a6ad-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6a6ad-123">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a6ad-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
