---
title: "IMetaDataEmit::DeletePinvokeMap – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1479c3fb19feec0e42ee4aec8544a35ce51350a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="4d02a-102">IMetaDataEmit::DeletePinvokeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="4d02a-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="4d02a-103">Zničí metadata PInvoke mapování pro objekt, který odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="4d02a-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d02a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d02a-104">Syntax</span></span>  
  
```  
HRESULT DeletePinvokeMap (   
    [in]  mdToken     tk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d02a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d02a-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="4d02a-106">[v] `mdFieldDef` Nebo `mdMethodDef` token, který představuje objekt, pro kterou chcete odstranit metadata PInvoke mapování.</span><span class="sxs-lookup"><span data-stu-id="4d02a-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d02a-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d02a-107">Requirements</span></span>  
 <span data-ttu-id="4d02a-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d02a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d02a-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4d02a-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4d02a-110">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4d02a-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4d02a-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d02a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d02a-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d02a-112">See Also</span></span>  
 [<span data-ttu-id="4d02a-113">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d02a-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="4d02a-114">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d02a-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
