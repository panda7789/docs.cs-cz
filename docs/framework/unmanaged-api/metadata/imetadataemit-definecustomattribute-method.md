---
title: IMetaDataEmit::DefineCustomAttribute – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineCustomAttribute
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineCustomAttribute
helpviewer_keywords:
- DefineCustomAttribute method [.NET Framework metadata]
- IMetaDataEmit::DefineCustomAttribute method [.NET Framework metadata]
ms.assetid: 7dd14854-b756-4401-b167-88ca576dc8f0
topic_type:
- apiref
ms.openlocfilehash: e6a732b98ae02ba2b273b45921b7de61ab4fd29f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432636"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="ecea6-102">IMetaDataEmit::DefineCustomAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="ecea6-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="ecea6-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span><span class="sxs-lookup"><span data-stu-id="ecea6-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecea6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecea6-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineCustomAttribute (   
    [in]  mdToken     tkObj,   
    [in]  mdToken     tkType,   
    [in]  void const  *pCustomAttribute,   
    [in]  ULONG       cbCustomAttribute,   
    [out] mdCustomAttribute *pcv   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecea6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ecea6-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="ecea6-106">[in] The token for the owner item.</span><span class="sxs-lookup"><span data-stu-id="ecea6-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="ecea6-107">[in] The token that identifies the custom attribute.</span><span class="sxs-lookup"><span data-stu-id="ecea6-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="ecea6-108">[in] A pointer to the custom attribute.</span><span class="sxs-lookup"><span data-stu-id="ecea6-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="ecea6-109">[in] The count of bytes in `pCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="ecea6-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="ecea6-110">[out] The `mdCustomAttribute` token assigned.</span><span class="sxs-lookup"><span data-stu-id="ecea6-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecea6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ecea6-111">Requirements</span></span>  
 <span data-ttu-id="ecea6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecea6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecea6-113">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ecea6-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ecea6-114">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ecea6-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecea6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecea6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecea6-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ecea6-116">See also</span></span>

- [<span data-ttu-id="ecea6-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ecea6-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ecea6-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ecea6-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
