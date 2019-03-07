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
ms.openlocfilehash: 1159e91004152b6c1393b87f25ff7964456adffc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498221"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="3c16e-102">IMetaDataEmit::SetEventProps – metoda</span><span class="sxs-lookup"><span data-stu-id="3c16e-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="3c16e-103">Nastaví nebo aktualizuje zadanou funkci události definované v předchozím volání [imetadataemit::defineevent –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="3c16e-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c16e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c16e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="3c16e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c16e-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="3c16e-106">[in] Token, který událost.</span><span class="sxs-lookup"><span data-stu-id="3c16e-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="3c16e-107">[in] Příznaky událostí.</span><span class="sxs-lookup"><span data-stu-id="3c16e-107">[in] Event flags.</span></span> <span data-ttu-id="3c16e-108">To je bitová maska z `CorEventAttr` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3c16e-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="3c16e-109">[in] Token pro třídy události.</span><span class="sxs-lookup"><span data-stu-id="3c16e-109">[in] The token for the event class.</span></span> <span data-ttu-id="3c16e-110">Je to `mdTypeDef` nebo `mdTypeRef` token.</span><span class="sxs-lookup"><span data-stu-id="3c16e-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="3c16e-111">[in] Metoda použitá k přihlášení k odběru událostí, nebo hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="3c16e-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="3c16e-112">[in] Metoda použitá k odhlášení odběru událostí, nebo hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="3c16e-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="3c16e-113">[in] Metoda použitá pro vyvolání události (prostřednictvím odvozené třídy).</span><span class="sxs-lookup"><span data-stu-id="3c16e-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="3c16e-114">[in] Pole tokenů pro jiné metody přidružené k události.</span><span class="sxs-lookup"><span data-stu-id="3c16e-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="3c16e-115">Poslední element pole musí být `mdMethodDefNil`.</span><span class="sxs-lookup"><span data-stu-id="3c16e-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c16e-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3c16e-116">Requirements</span></span>  
 <span data-ttu-id="3c16e-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c16e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c16e-118">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3c16e-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3c16e-119">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3c16e-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c16e-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c16e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c16e-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c16e-121">See also</span></span>
- [<span data-ttu-id="3c16e-122">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c16e-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3c16e-123">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c16e-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
