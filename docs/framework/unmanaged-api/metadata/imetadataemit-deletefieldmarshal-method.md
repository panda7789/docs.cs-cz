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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf9cc16ba2702e814f27adb009a5e9b63acc97e3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500187"
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="390c1-102">IMetaDataEmit::DeleteFieldMarshal – metoda</span><span class="sxs-lookup"><span data-stu-id="390c1-102">IMetaDataEmit::DeleteFieldMarshal Method</span></span>
<span data-ttu-id="390c1-103">Zničí PInvoke zařazování podpis metadat pro objekt odkazovaný zadaným parametrem zadaného tokenu.</span><span class="sxs-lookup"><span data-stu-id="390c1-103">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="390c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="390c1-104">Syntax</span></span>  
  
```  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="390c1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="390c1-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="390c1-106">[in] `mdFieldDef` Nebo `mdParamDef` token, který představuje pole nebo parametr, pro kterou chcete odstranit zařazování podpis metadat.</span><span class="sxs-lookup"><span data-stu-id="390c1-106">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="390c1-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="390c1-107">Requirements</span></span>  
 <span data-ttu-id="390c1-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="390c1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="390c1-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="390c1-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="390c1-110">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="390c1-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="390c1-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="390c1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="390c1-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="390c1-112">See also</span></span>
- [<span data-ttu-id="390c1-113">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="390c1-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="390c1-114">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="390c1-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
