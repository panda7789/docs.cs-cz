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
ms.workload: dotnet
ms.openlocfilehash: 053601376f8b75e5469a3ef8a3d890a6c6620e28
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="ab9de-102">IMetaDataEmit::DefineCustomAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="ab9de-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="ab9de-103">Vytvoří definici pro vlastní atribut podpisem Zadaná metadata, připojí se k zadaný objekt a získá token tuto definici vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="ab9de-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab9de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab9de-104">Syntax</span></span>  
  
```  
HRESULT DefineCustomAttribute (   
    [in]  mdToken     tkObj,   
    [in]  mdToken     tkType,   
    [in]  void const  *pCustomAttribute,   
    [in]  ULONG       cbCustomAttribute,   
    [out] mdCustomAttribute *pcv   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab9de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab9de-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="ab9de-106">[v] Token pro položku vlastníka.</span><span class="sxs-lookup"><span data-stu-id="ab9de-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="ab9de-107">[v] Token, který identifikuje vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="ab9de-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="ab9de-108">[v] Ukazatel na vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="ab9de-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="ab9de-109">[v] Počet bajtů v `pCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="ab9de-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="ab9de-110">[out] `mdCustomAttribute` Token přiřazený.</span><span class="sxs-lookup"><span data-stu-id="ab9de-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab9de-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ab9de-111">Requirements</span></span>  
 <span data-ttu-id="ab9de-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab9de-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab9de-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ab9de-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ab9de-114">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ab9de-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab9de-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab9de-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab9de-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab9de-116">See Also</span></span>  
 [<span data-ttu-id="ab9de-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab9de-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="ab9de-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab9de-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
