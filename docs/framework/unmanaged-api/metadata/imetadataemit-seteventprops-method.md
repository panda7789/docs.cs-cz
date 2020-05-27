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
ms.openlocfilehash: 720133e64c02aa09c9ff7e43a20630b0d55c1acf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008752"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="233bb-102">IMetaDataEmit::SetEventProps – metoda</span><span class="sxs-lookup"><span data-stu-id="233bb-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="233bb-103">Nastaví nebo aktualizuje zadanou funkci události definované předchozím voláním metody [IMetaDataEmit::D efineevent](imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="233bb-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="233bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="233bb-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="233bb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="233bb-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="233bb-106">pro Token události</span><span class="sxs-lookup"><span data-stu-id="233bb-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="233bb-107">pro Příznaky události.</span><span class="sxs-lookup"><span data-stu-id="233bb-107">[in] Event flags.</span></span> <span data-ttu-id="233bb-108">Toto je Bitová maska `CorEventAttr` hodnot.</span><span class="sxs-lookup"><span data-stu-id="233bb-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="233bb-109">pro Token pro třídu Event</span><span class="sxs-lookup"><span data-stu-id="233bb-109">[in] The token for the event class.</span></span> <span data-ttu-id="233bb-110">Toto je buď `mdTypeDef` token, nebo `mdTypeRef` .</span><span class="sxs-lookup"><span data-stu-id="233bb-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="233bb-111">pro Metoda použitá k přihlášení k odběru události nebo hodnota null.</span><span class="sxs-lookup"><span data-stu-id="233bb-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="233bb-112">pro Metoda použitá k odhlášení odběru události nebo hodnota null.</span><span class="sxs-lookup"><span data-stu-id="233bb-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="233bb-113">pro Použitá metoda (odvozenou třídou) k vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="233bb-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="233bb-114">pro Pole tokenů pro jiné metody přidružené k události.</span><span class="sxs-lookup"><span data-stu-id="233bb-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="233bb-115">Poslední prvek pole musí být `mdMethodDefNil` .</span><span class="sxs-lookup"><span data-stu-id="233bb-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="233bb-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="233bb-116">Requirements</span></span>  
 <span data-ttu-id="233bb-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="233bb-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="233bb-118">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="233bb-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="233bb-119">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="233bb-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="233bb-120">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="233bb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="233bb-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="233bb-121">See also</span></span>

- [<span data-ttu-id="233bb-122">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="233bb-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="233bb-123">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="233bb-123">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
