---
title: IMetaDataEmit::SetParent – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParent
helpviewer_keywords:
- SetParent method [.NET Framework metadata]
- IMetaDataEmit::SetParent method [.NET Framework metadata]
ms.assetid: 02a02ff7-ae0e-4692-a20e-372405f23052
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1a37edd38cd8dc6971ee9185f73d6c6d8ab5332b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657128"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="e74f6-102">IMetaDataEmit::SetParent – metoda</span><span class="sxs-lookup"><span data-stu-id="e74f6-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="e74f6-103">Zjistí, že zadaný člen podle předchozího volání [imetadataemit::definememberref –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), je členem zadaného typu definované předchozím volání [imetadataemit::definetypedef –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="e74f6-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e74f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e74f6-104">Syntax</span></span>  
  
```  
HRESULT SetParent (   
    [in]  mdMemberRef mr,   
    [in]  mdToken     tk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e74f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e74f6-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="e74f6-106">[in] `mdMemberRef` Token pro příjem novou nadřazenou položku.</span><span class="sxs-lookup"><span data-stu-id="e74f6-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="e74f6-107">[in] `mdToken` Pro novou nadřazenou položku.</span><span class="sxs-lookup"><span data-stu-id="e74f6-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e74f6-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e74f6-108">Requirements</span></span>  
 <span data-ttu-id="e74f6-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e74f6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e74f6-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e74f6-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e74f6-111">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e74f6-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e74f6-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e74f6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e74f6-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e74f6-113">See also</span></span>
- [<span data-ttu-id="e74f6-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e74f6-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e74f6-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e74f6-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
