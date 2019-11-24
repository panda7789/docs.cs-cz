---
title: IMetaDataEmit::DeleteFieldMarshal – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteFieldMarshal
helpviewer_keywords:
- IMetaDataEmit::DeleteFieldMarshal method [.NET Framework metadata]
- DeleteFieldMarshal method [.NET Framework metadata]
ms.assetid: 7c75aef9-c742-4b33-a14b-56ff94b0f725
topic_type:
- apiref
ms.openlocfilehash: 652169c67461c1663c005dd014290c4cf2d993ba
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434368"
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="e7531-102">IMetaDataEmit::DeleteFieldMarshal – metoda</span><span class="sxs-lookup"><span data-stu-id="e7531-102">IMetaDataEmit::DeleteFieldMarshal Method</span></span>
<span data-ttu-id="e7531-103">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span><span class="sxs-lookup"><span data-stu-id="e7531-103">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7531-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7531-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7531-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7531-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="e7531-106">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span><span class="sxs-lookup"><span data-stu-id="e7531-106">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7531-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7531-107">Requirements</span></span>  
 <span data-ttu-id="e7531-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7531-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7531-109">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e7531-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e7531-110">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e7531-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e7531-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7531-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7531-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7531-112">See also</span></span>

- [<span data-ttu-id="e7531-113">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e7531-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e7531-114">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e7531-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
