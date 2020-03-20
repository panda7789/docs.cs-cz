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
ms.openlocfilehash: a9598be850604f16ee8cc62187e1fed7ecf3a7e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175847"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="80359-102">IMetaDataEmit::DefineEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="80359-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="80359-103">Vytvoří definici události se zadaným podpisem metadat a získá token pro tuto definici události.</span><span class="sxs-lookup"><span data-stu-id="80359-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80359-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80359-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="80359-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80359-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="80359-106">[v] Token pro cílovou třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="80359-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="80359-107">Toto je `mdTypeDef` `mdTypeDefNil` buď nebo token.</span><span class="sxs-lookup"><span data-stu-id="80359-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="80359-108">[v] Název události.</span><span class="sxs-lookup"><span data-stu-id="80359-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="80359-109">[v] Příznaky události.</span><span class="sxs-lookup"><span data-stu-id="80359-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="80359-110">[v] Token pro třídu události.</span><span class="sxs-lookup"><span data-stu-id="80359-110">[in] The token for the event class.</span></span> <span data-ttu-id="80359-111">Toto `mdTypeDef`je `mdTypeRef`, a `mdTokenNil` nebo token.</span><span class="sxs-lookup"><span data-stu-id="80359-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="80359-112">[v] Metoda použitá k přihlášení k odběru události nebo null.</span><span class="sxs-lookup"><span data-stu-id="80359-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="80359-113">[v] Metoda použitá k odhlášení z odběru události nebo null.</span><span class="sxs-lookup"><span data-stu-id="80359-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="80359-114">[v] Metoda použitá (odvozenou třídou) k navojení události.</span><span class="sxs-lookup"><span data-stu-id="80359-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="80359-115">[v] Pole tokenů pro jiné metody přidružené k události.</span><span class="sxs-lookup"><span data-stu-id="80359-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="80359-116">Pole je ukončeno `mdMethodDefNil` tokenem.</span><span class="sxs-lookup"><span data-stu-id="80359-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="80359-117">[out] Token metadat přiřazený k události.</span><span class="sxs-lookup"><span data-stu-id="80359-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80359-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="80359-118">Requirements</span></span>  
 <span data-ttu-id="80359-119">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80359-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80359-120">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="80359-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80359-121">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="80359-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80359-122">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80359-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80359-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="80359-123">See also</span></span>

- [<span data-ttu-id="80359-124">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="80359-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="80359-125">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="80359-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
