---
title: "IMetaDataEmit::SetCustomAttributeValue – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetCustomAttributeValue
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetCustomAttributeValue
helpviewer_keywords:
- SetCustomAttributeValue method [.NET Framework metadata]
- IMetaDataEmit::SetCustomAttributeValue method [.NET Framework metadata]
ms.assetid: f721c863-9642-4e64-917a-65f9e55c25b9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 30538b0f6f6aa196edf8373f5f4e6f09ba903223
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="eae6a-102">IMetaDataEmit::SetCustomAttributeValue – metoda</span><span class="sxs-lookup"><span data-stu-id="eae6a-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>
<span data-ttu-id="eae6a-103">Nastaví nebo aktualizuje hodnota vlastního atributu definované předchozí volání [imetadataemit::definecustomattribute –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span><span class="sxs-lookup"><span data-stu-id="eae6a-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eae6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eae6a-104">Syntax</span></span>  
  
```  
HRESULT SetCustomAttributeValue (   
    [in]  mdCustomAttribute       pcv,   
    [in]  void const              *pCustomAttribute,    
    [in]  ULONG                   cbCustomAttribute   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eae6a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eae6a-105">Parameters</span></span>  
 `pcv`  
 <span data-ttu-id="eae6a-106">[v] Token vlastní atribut target.</span><span class="sxs-lookup"><span data-stu-id="eae6a-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="eae6a-107">[v] Ukazatel na pole, které obsahuje vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="eae6a-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="eae6a-108">[v] Velikost v bajtech, vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="eae6a-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eae6a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eae6a-109">Requirements</span></span>  
 <span data-ttu-id="eae6a-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eae6a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eae6a-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="eae6a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eae6a-112">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eae6a-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eae6a-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eae6a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eae6a-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="eae6a-114">See Also</span></span>  
 [<span data-ttu-id="eae6a-115">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eae6a-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="eae6a-116">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eae6a-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
