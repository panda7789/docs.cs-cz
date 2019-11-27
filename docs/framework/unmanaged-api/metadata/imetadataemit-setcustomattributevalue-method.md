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
ms.openlocfilehash: fd5e71071de9e6afebc8f1848e0af8835f22c9bf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448120"
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="e15e2-102">IMetaDataEmit::SetCustomAttributeValue – metoda</span><span class="sxs-lookup"><span data-stu-id="e15e2-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>
<span data-ttu-id="e15e2-103">Nastaví nebo aktualizuje hodnotu vlastního atributu definovaného předchozím voláním [IMetaDataEmit::D efinecustomattribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span><span class="sxs-lookup"><span data-stu-id="e15e2-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e15e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e15e2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCustomAttributeValue (   
    [in]  mdCustomAttribute       pcv,   
    [in]  void const              *pCustomAttribute,    
    [in]  ULONG                   cbCustomAttribute   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e15e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e15e2-105">Parameters</span></span>  
 `pcv`  
 <span data-ttu-id="e15e2-106">pro Token cílového vlastního atributu</span><span class="sxs-lookup"><span data-stu-id="e15e2-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="e15e2-107">pro Ukazatel na pole, které obsahuje vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="e15e2-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="e15e2-108">pro Velikost vlastního atributu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="e15e2-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e15e2-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e15e2-109">Requirements</span></span>  
 <span data-ttu-id="e15e2-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e15e2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e15e2-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e15e2-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e15e2-112">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="e15e2-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e15e2-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e15e2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e15e2-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e15e2-114">See also</span></span>

- [<span data-ttu-id="e15e2-115">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e15e2-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e15e2-116">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e15e2-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
