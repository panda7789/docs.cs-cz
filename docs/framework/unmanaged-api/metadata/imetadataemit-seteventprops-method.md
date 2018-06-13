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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 42dc78ff3c58b67801cd99512781d8c8509dd272
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447337"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="31e1c-102">IMetaDataEmit::SetEventProps – metoda</span><span class="sxs-lookup"><span data-stu-id="31e1c-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="31e1c-103">Nastaví nebo aktualizuje určenou funkci události definované předchozí volání [imetadataemit::defineevent –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="31e1c-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31e1c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31e1c-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="31e1c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="31e1c-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="31e1c-106">[v] Token událostí.</span><span class="sxs-lookup"><span data-stu-id="31e1c-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="31e1c-107">[v] Příznaky událostí.</span><span class="sxs-lookup"><span data-stu-id="31e1c-107">[in] Event flags.</span></span> <span data-ttu-id="31e1c-108">Toto je bitová maska s `CorEventAttr` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="31e1c-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="31e1c-109">[v] Token pro třídy události.</span><span class="sxs-lookup"><span data-stu-id="31e1c-109">[in] The token for the event class.</span></span> <span data-ttu-id="31e1c-110">To znamená buď `mdTypeDef` nebo `mdTypeRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="31e1c-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="31e1c-111">[v] Metoda použitá k odběru události, nebo hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="31e1c-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="31e1c-112">[v] Metoda použitá k odhlášení odběru událostí, nebo hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="31e1c-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="31e1c-113">[v] Metoda použitá k vyvolání události (podle odvozené třídy).</span><span class="sxs-lookup"><span data-stu-id="31e1c-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="31e1c-114">[v] Pole tokeny pro jiné metody přidružený k události.</span><span class="sxs-lookup"><span data-stu-id="31e1c-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="31e1c-115">Musí být posledním prvkem pole `mdMethodDefNil`.</span><span class="sxs-lookup"><span data-stu-id="31e1c-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31e1c-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="31e1c-116">Requirements</span></span>  
 <span data-ttu-id="31e1c-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31e1c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31e1c-118">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="31e1c-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="31e1c-119">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="31e1c-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31e1c-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31e1c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31e1c-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="31e1c-121">See Also</span></span>  
 [<span data-ttu-id="31e1c-122">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="31e1c-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="31e1c-123">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="31e1c-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
