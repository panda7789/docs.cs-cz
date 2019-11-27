---
title: IMetaDataEmit::DefineEvent – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type:
- apiref
ms.openlocfilehash: 6966d0ad2fefd8401b19d8e8dcf7776799a066b2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432562"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="333ed-102">IMetaDataEmit::DefineEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="333ed-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="333ed-103">Vytvoří definici události se zadaným podpisem metadat a získá token této definice události.</span><span class="sxs-lookup"><span data-stu-id="333ed-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="333ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="333ed-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineEvent (   
    [in]  mdTypeDef    td,   
    [in]  LPCWSTR      szEvent,   
    [in]  DWORD        dwEventFlags,   
    [in]  mdToken      tkEventType,   
    [in]  mdMethodDef  mdAddOn,   
    [in]  mdMethodDef  mdRemoveOn,   
    [in]  mdMethodDef  mdFire,   
    [in]  mdMethodDef  rmdOtherMethods[],   
    [out] mdEvent      *pmdEvent   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="333ed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="333ed-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="333ed-106">pro Token pro cílovou třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="333ed-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="333ed-107">Jedná se o token `mdTypeDef` nebo `mdTypeDefNil`.</span><span class="sxs-lookup"><span data-stu-id="333ed-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="333ed-108">pro Název události.</span><span class="sxs-lookup"><span data-stu-id="333ed-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="333ed-109">pro Příznaky události.</span><span class="sxs-lookup"><span data-stu-id="333ed-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="333ed-110">pro Token pro třídu Event</span><span class="sxs-lookup"><span data-stu-id="333ed-110">[in] The token for the event class.</span></span> <span data-ttu-id="333ed-111">Toto je `mdTypeDef`, `mdTypeRef`nebo token `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="333ed-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="333ed-112">pro Metoda použitá k přihlášení k odběru události nebo hodnota null.</span><span class="sxs-lookup"><span data-stu-id="333ed-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="333ed-113">pro Metoda použitá k odhlášení odběru události nebo hodnota null.</span><span class="sxs-lookup"><span data-stu-id="333ed-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="333ed-114">pro Použitá metoda (odvozenou třídou) k vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="333ed-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="333ed-115">pro Pole tokenů pro jiné metody přidružené k události.</span><span class="sxs-lookup"><span data-stu-id="333ed-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="333ed-116">Pole je ukončeno pomocí `mdMethodDefNil`ho tokenu.</span><span class="sxs-lookup"><span data-stu-id="333ed-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="333ed-117">mimo Token metadat přiřazený k události</span><span class="sxs-lookup"><span data-stu-id="333ed-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="333ed-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="333ed-118">Requirements</span></span>  
 <span data-ttu-id="333ed-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="333ed-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="333ed-120">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="333ed-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="333ed-121">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="333ed-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="333ed-122">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="333ed-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="333ed-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="333ed-123">See also</span></span>

- [<span data-ttu-id="333ed-124">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="333ed-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="333ed-125">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="333ed-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
