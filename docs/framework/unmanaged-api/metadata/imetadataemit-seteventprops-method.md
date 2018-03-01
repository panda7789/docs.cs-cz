---
title: "IMetaDataEmit::SetEventProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f8e2089c3f4b4e7677c2ddb9eabc8ee08cfd3695
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="41c5a-102">IMetaDataEmit::SetEventProps – metoda</span><span class="sxs-lookup"><span data-stu-id="41c5a-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="41c5a-103">Nastaví nebo aktualizuje určenou funkci události definované předchozí volání [imetadataemit::defineevent –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="41c5a-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41c5a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41c5a-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="41c5a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="41c5a-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="41c5a-106">[v] Token událostí.</span><span class="sxs-lookup"><span data-stu-id="41c5a-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="41c5a-107">[v] Příznaky událostí.</span><span class="sxs-lookup"><span data-stu-id="41c5a-107">[in] Event flags.</span></span> <span data-ttu-id="41c5a-108">Toto je bitová maska s `CorEventAttr` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="41c5a-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="41c5a-109">[v] Token pro třídy události.</span><span class="sxs-lookup"><span data-stu-id="41c5a-109">[in] The token for the event class.</span></span> <span data-ttu-id="41c5a-110">To znamená buď `mdTypeDef` nebo `mdTypeRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="41c5a-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="41c5a-111">[v] Metoda použitá k odběru události, nebo hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="41c5a-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="41c5a-112">[v] Metoda použitá k odhlášení odběru událostí, nebo hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="41c5a-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="41c5a-113">[v] Metoda použitá k vyvolání události (podle odvozené třídy).</span><span class="sxs-lookup"><span data-stu-id="41c5a-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="41c5a-114">[v] Pole tokeny pro jiné metody přidružený k události.</span><span class="sxs-lookup"><span data-stu-id="41c5a-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="41c5a-115">Musí být posledním prvkem pole `mdMethodDefNil`.</span><span class="sxs-lookup"><span data-stu-id="41c5a-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41c5a-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="41c5a-116">Requirements</span></span>  
 <span data-ttu-id="41c5a-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41c5a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41c5a-118">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="41c5a-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="41c5a-119">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="41c5a-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41c5a-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41c5a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41c5a-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="41c5a-121">See Also</span></span>  
 [<span data-ttu-id="41c5a-122">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="41c5a-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="41c5a-123">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="41c5a-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
