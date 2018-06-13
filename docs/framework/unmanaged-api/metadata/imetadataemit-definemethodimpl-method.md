---
title: IMetaDataEmit::DefineMethodImpl – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethodImpl
helpviewer_keywords:
- DefineMethodImpl method [.NET Framework metadata]
- IMetaDataEmit::DefineMethodImpl method [.NET Framework metadata]
ms.assetid: 9dcc8b3d-33ee-4c7c-8d6f-322c57b94a0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2ab66fecfaa66b5c56690950f6b19ecfd7e85e33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443986"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="bb6b8-102">IMetaDataEmit::DefineMethodImpl – metoda</span><span class="sxs-lookup"><span data-stu-id="bb6b8-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="bb6b8-103">Vytvoří definici implementace metody zděděno z rozhraní a vrátí token tuto definici implementace metod.</span><span class="sxs-lookup"><span data-stu-id="bb6b8-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb6b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb6b8-104">Syntax</span></span>  
  
```  
HRESULT DefineMethodImpl (   
    [in]  mdTypeDef         td,   
    [in]  mdToken           tkBody,   
    [in]  mdToken           tkDecl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb6b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb6b8-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="bb6b8-106">[v] `mdTypedef` Tokenu z implementující třídu.</span><span class="sxs-lookup"><span data-stu-id="bb6b8-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="bb6b8-107">[v] `mdMethodDef` Nebo `mdMethodRef` těla kód tokenu.</span><span class="sxs-lookup"><span data-stu-id="bb6b8-107">[in] The `mdMethodDef` or `mdMethodRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="bb6b8-108">[v] `mdMethodDef` Nebo `mdMethodRef` tokenu z se implementuje metodu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bb6b8-108">[in] The `mdMethodDef` or `mdMethodRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb6b8-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb6b8-109">Requirements</span></span>  
 <span data-ttu-id="bb6b8-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb6b8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb6b8-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bb6b8-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bb6b8-112">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bb6b8-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb6b8-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb6b8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb6b8-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb6b8-114">See Also</span></span>  
 [<span data-ttu-id="bb6b8-115">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb6b8-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="bb6b8-116">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb6b8-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
