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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 48055103b49b4c61bb7561f2d4aa6c8daae07ae2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62044210"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="23a3b-102">IMetaDataEmit::DefineEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="23a3b-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="23a3b-103">Vytvoří definici pro události s podpisem Zadaná metadata a získá token pro tuto definici událostí.</span><span class="sxs-lookup"><span data-stu-id="23a3b-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23a3b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23a3b-104">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="23a3b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="23a3b-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="23a3b-106">[in] Token pro cílovou třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="23a3b-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="23a3b-107">Je to `mdTypeDef` nebo `mdTypeDefNil` token.</span><span class="sxs-lookup"><span data-stu-id="23a3b-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="23a3b-108">[in] Název události.</span><span class="sxs-lookup"><span data-stu-id="23a3b-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="23a3b-109">[in] Příznaky událostí.</span><span class="sxs-lookup"><span data-stu-id="23a3b-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="23a3b-110">[in] Token pro třídy události.</span><span class="sxs-lookup"><span data-stu-id="23a3b-110">[in] The token for the event class.</span></span> <span data-ttu-id="23a3b-111">Jde `mdTypeDef`, `mdTypeRef`, nebo `mdTokenNil` token.</span><span class="sxs-lookup"><span data-stu-id="23a3b-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="23a3b-112">[in] Metoda použitá k přihlášení k odběru událostí, nebo hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="23a3b-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="23a3b-113">[in] Metoda použitá k odhlášení odběru událostí, nebo hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="23a3b-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="23a3b-114">[in] Metoda použitá pro vyvolání události (prostřednictvím odvozené třídy).</span><span class="sxs-lookup"><span data-stu-id="23a3b-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="23a3b-115">[in] Pole tokenů pro jiné metody přidružené k události.</span><span class="sxs-lookup"><span data-stu-id="23a3b-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="23a3b-116">Pole je přerušen skrze `mdMethodDefNil` token.</span><span class="sxs-lookup"><span data-stu-id="23a3b-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="23a3b-117">[out] Token metadat přiřazený k této události.</span><span class="sxs-lookup"><span data-stu-id="23a3b-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23a3b-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="23a3b-118">Requirements</span></span>  
 <span data-ttu-id="23a3b-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23a3b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23a3b-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="23a3b-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="23a3b-121">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="23a3b-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="23a3b-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23a3b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23a3b-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="23a3b-123">See also</span></span>

- [<span data-ttu-id="23a3b-124">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="23a3b-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="23a3b-125">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="23a3b-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
