---
title: "IMetaDataEmit::DefineCustomAttribute – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineCustomAttribute
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineCustomAttribute
helpviewer_keywords:
- DefineCustomAttribute method [.NET Framework metadata]
- IMetaDataEmit::DefineCustomAttribute method [.NET Framework metadata]
ms.assetid: 7dd14854-b756-4401-b167-88ca576dc8f0
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1c4c00480571b4160d7442aeafea088fe8d04ba6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="985c0-102">IMetaDataEmit::DefineCustomAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="985c0-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="985c0-103">Vytvoří definici pro vlastní atribut podpisem Zadaná metadata, připojí se k zadaný objekt a získá token tuto definici vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="985c0-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="985c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="985c0-104">Syntax</span></span>  
  
```  
HRESULT DefineCustomAttribute (   
    [in]  mdToken     tkObj,   
    [in]  mdToken     tkType,   
    [in]  void const  *pCustomAttribute,   
    [in]  ULONG       cbCustomAttribute,   
    [out] mdCustomAttribute *pcv   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="985c0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="985c0-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="985c0-106">[v] Token pro položku vlastníka.</span><span class="sxs-lookup"><span data-stu-id="985c0-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="985c0-107">[v] Token, který identifikuje vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="985c0-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="985c0-108">[v] Ukazatel na vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="985c0-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="985c0-109">[v] Počet bajtů v `pCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="985c0-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="985c0-110">[out] `mdCustomAttribute` Token přiřazený.</span><span class="sxs-lookup"><span data-stu-id="985c0-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="985c0-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="985c0-111">Requirements</span></span>  
 <span data-ttu-id="985c0-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="985c0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="985c0-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="985c0-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="985c0-114">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="985c0-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="985c0-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="985c0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="985c0-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="985c0-116">See Also</span></span>  
 [<span data-ttu-id="985c0-117">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="985c0-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="985c0-118">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="985c0-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
