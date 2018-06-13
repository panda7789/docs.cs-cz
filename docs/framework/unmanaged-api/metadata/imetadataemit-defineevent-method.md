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
ms.openlocfilehash: ce94765467899ac7c906b0dfcdf0ceb78c659b5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448201"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="dca86-102">IMetaDataEmit::DefineEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="dca86-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="dca86-103">Vytvoří definici pro události s podpisem Zadaná metadata a získá token tuto definici událostí.</span><span class="sxs-lookup"><span data-stu-id="dca86-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dca86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dca86-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="dca86-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dca86-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="dca86-106">[v] Token pro danou cílovou třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dca86-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="dca86-107">To znamená buď `mdTypeDef` nebo `mdTypeDefNil` tokenu.</span><span class="sxs-lookup"><span data-stu-id="dca86-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="dca86-108">[v] Název události.</span><span class="sxs-lookup"><span data-stu-id="dca86-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="dca86-109">[v] Příznaky událostí.</span><span class="sxs-lookup"><span data-stu-id="dca86-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="dca86-110">[v] Token pro třídy události.</span><span class="sxs-lookup"><span data-stu-id="dca86-110">[in] The token for the event class.</span></span> <span data-ttu-id="dca86-111">Toto je `mdTypeDef`, `mdTypeRef`, nebo `mdTokenNil` tokenu.</span><span class="sxs-lookup"><span data-stu-id="dca86-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="dca86-112">[v] Metoda použitá k odběru události, nebo hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="dca86-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="dca86-113">[v] Metoda použitá k odhlášení odběru událostí, nebo hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="dca86-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="dca86-114">[v] Metoda použitá k vyvolání události (podle odvozené třídy).</span><span class="sxs-lookup"><span data-stu-id="dca86-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="dca86-115">[v] Pole tokeny pro jiné metody přidružený k události.</span><span class="sxs-lookup"><span data-stu-id="dca86-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="dca86-116">Toto pole je byla ukončena s `mdMethodDefNil` tokenu.</span><span class="sxs-lookup"><span data-stu-id="dca86-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="dca86-117">[out] Metadata token přiřazené k události.</span><span class="sxs-lookup"><span data-stu-id="dca86-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dca86-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dca86-118">Requirements</span></span>  
 <span data-ttu-id="dca86-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dca86-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dca86-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dca86-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dca86-121">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dca86-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dca86-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dca86-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dca86-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="dca86-123">See Also</span></span>  
 [<span data-ttu-id="dca86-124">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dca86-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="dca86-125">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dca86-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
