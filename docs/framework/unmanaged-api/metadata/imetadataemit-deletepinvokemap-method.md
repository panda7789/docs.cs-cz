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
ms.openlocfilehash: 5775c249236fdbe488ce11be0c664d2073ccfb67
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57477072"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="9f8b7-102">IMetaDataEmit::DeletePinvokeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="9f8b7-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="9f8b7-103">Zničí metadat PInvoke mapování pro objekt odkazovaný zadaným parametrem zadaného tokenu.</span><span class="sxs-lookup"><span data-stu-id="9f8b7-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f8b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f8b7-104">Syntax</span></span>  
  
```  
HRESULT DeletePinvokeMap (   
    [in]  mdToken     tk   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f8b7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f8b7-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="9f8b7-106">[in] `mdFieldDef` Nebo `mdMethodDef` token, který představuje objekt, pro kterou chcete odstranit mapování metadat PInvoke.</span><span class="sxs-lookup"><span data-stu-id="9f8b7-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f8b7-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9f8b7-107">Requirements</span></span>  
 <span data-ttu-id="9f8b7-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f8b7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f8b7-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9f8b7-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9f8b7-110">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9f8b7-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9f8b7-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f8b7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f8b7-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f8b7-112">See also</span></span>
- [<span data-ttu-id="9f8b7-113">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9f8b7-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="9f8b7-114">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9f8b7-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
