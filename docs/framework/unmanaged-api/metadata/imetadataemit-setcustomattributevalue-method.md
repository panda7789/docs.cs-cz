---
title: IMetaDataEmit::SetCustomAttributeValue – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetCustomAttributeValue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetCustomAttributeValue
helpviewer_keywords:
- SetCustomAttributeValue method [.NET Framework metadata]
- IMetaDataEmit::SetCustomAttributeValue method [.NET Framework metadata]
ms.assetid: f721c863-9642-4e64-917a-65f9e55c25b9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6f9e684b90dcc7f0ff83962361486caf7e991568
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050074"
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="06d99-102">IMetaDataEmit::SetCustomAttributeValue – metoda</span><span class="sxs-lookup"><span data-stu-id="06d99-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>
<span data-ttu-id="06d99-103">Nastaví nebo aktualizuje hodnotu vlastního atributu určené předchozím volání [imetadataemit::definecustomattribute –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span><span class="sxs-lookup"><span data-stu-id="06d99-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06d99-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06d99-104">Syntax</span></span>  
  
```  
HRESULT SetCustomAttributeValue (   
    [in]  mdCustomAttribute       pcv,   
    [in]  void const              *pCustomAttribute,    
    [in]  ULONG                   cbCustomAttribute   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06d99-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06d99-105">Parameters</span></span>  
 `pcv`  
 <span data-ttu-id="06d99-106">[in] Token vlastní atribut target.</span><span class="sxs-lookup"><span data-stu-id="06d99-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="06d99-107">[in] Ukazatele na pole, která obsahuje vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="06d99-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="06d99-108">[in] Velikost v bajtech vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="06d99-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06d99-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="06d99-109">Requirements</span></span>  
 <span data-ttu-id="06d99-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06d99-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06d99-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="06d99-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="06d99-112">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="06d99-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="06d99-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06d99-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06d99-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06d99-114">See also</span></span>

- [<span data-ttu-id="06d99-115">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="06d99-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="06d99-116">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="06d99-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
