---
title: IMetaDataEmit::DeletePinvokeMap – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeletePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeletePinvokeMap
helpviewer_keywords:
- IMetaDataEmit::DeletePinvokeMap method [.NET Framework metadata]
- DeletePinvokeMap method [.NET Framework metadata]
ms.assetid: 3c4f6b54-5ce7-4a2a-83e1-6dec16441f50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c3b7c116410ce3309d970929580f4ec7f65bd657
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558279"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="d9828-102">IMetaDataEmit::DeletePinvokeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="d9828-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="d9828-103">Zničí metadat PInvoke mapování pro objekt odkazovaný zadaným parametrem zadaného tokenu.</span><span class="sxs-lookup"><span data-stu-id="d9828-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9828-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9828-104">Syntax</span></span>  
  
```  
HRESULT DeletePinvokeMap (   
    [in]  mdToken     tk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9828-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9828-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="d9828-106">[in] `mdFieldDef` Nebo `mdMethodDef` token, který představuje objekt, pro kterou chcete odstranit mapování metadat PInvoke.</span><span class="sxs-lookup"><span data-stu-id="d9828-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9828-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d9828-107">Requirements</span></span>  
 <span data-ttu-id="d9828-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9828-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9828-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d9828-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d9828-110">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d9828-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9828-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9828-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9828-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9828-112">See also</span></span>
- [<span data-ttu-id="d9828-113">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9828-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d9828-114">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9828-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
