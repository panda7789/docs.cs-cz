---
title: IMetaDataEmit::DeleteClassLayout – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteClassLayout
helpviewer_keywords:
- DeleteClassLayout method [.NET Framework metadata]
- IMetaDataEmit::DeleteClassLayout method [.NET Framework metadata]
ms.assetid: 65a4ad49-fa49-4b36-8ed1-76dd6a185ab4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 663f2de5acb3aac92c29a19f5f5db16b5355fe89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444780"
---
# <a name="imetadataemitdeleteclasslayout-method"></a><span data-ttu-id="eabf9-102">IMetaDataEmit::DeleteClassLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="eabf9-102">IMetaDataEmit::DeleteClassLayout Method</span></span>
<span data-ttu-id="eabf9-103">Zničí podpis třída rozložení metadata pro typu představovaný typem zadaný token.</span><span class="sxs-lookup"><span data-stu-id="eabf9-103">Destroys the class layout metadata signature for the type represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eabf9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eabf9-104">Syntax</span></span>  
  
```  
HRESULT DeleteClassLayout (  
    [in]  mdTypeDef   td  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eabf9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eabf9-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="eabf9-106">[v] `mdTypeDef` Metadata token, který představuje typ, pro které se odstraní třída rozložení.</span><span class="sxs-lookup"><span data-stu-id="eabf9-106">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eabf9-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eabf9-107">Requirements</span></span>  
 <span data-ttu-id="eabf9-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eabf9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eabf9-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="eabf9-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eabf9-110">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eabf9-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eabf9-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eabf9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eabf9-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="eabf9-112">See Also</span></span>  
 [<span data-ttu-id="eabf9-113">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eabf9-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="eabf9-114">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eabf9-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
