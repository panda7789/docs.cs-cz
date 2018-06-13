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
ms.openlocfilehash: fdaa6aab28eb82450db7b9f946e033bfad55faf5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446066"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="963bf-102">IMetaDataEmit::SetParent – metoda</span><span class="sxs-lookup"><span data-stu-id="963bf-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="963bf-103">Zjistí, že zadaný člen, jak je definována předchozí volání [imetadataemit::definememberref –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), je členem skupiny zadaný typ podle definice předchozí volání [imetadataemit::definetypedef –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="963bf-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="963bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="963bf-104">Syntax</span></span>  
  
```  
HRESULT SetParent (   
    [in]  mdMemberRef mr,   
    [in]  mdToken     tk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="963bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="963bf-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="963bf-106">[v] `mdMemberRef` Token pro příjem novou nadřazenou položku.</span><span class="sxs-lookup"><span data-stu-id="963bf-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="963bf-107">[v] `mdToken` Pro novou nadřazenou položku.</span><span class="sxs-lookup"><span data-stu-id="963bf-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="963bf-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="963bf-108">Requirements</span></span>  
 <span data-ttu-id="963bf-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="963bf-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="963bf-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="963bf-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="963bf-111">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="963bf-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="963bf-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="963bf-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="963bf-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="963bf-113">See Also</span></span>  
 [<span data-ttu-id="963bf-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="963bf-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="963bf-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="963bf-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
