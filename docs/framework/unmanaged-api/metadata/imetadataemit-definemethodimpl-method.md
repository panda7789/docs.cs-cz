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
ms.openlocfilehash: 64d76efa8c2f29fda559e5c84217b865540027ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175821"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="92237-102">IMetaDataEmit::DefineMethodImpl – metoda</span><span class="sxs-lookup"><span data-stu-id="92237-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="92237-103">Vytvoří definici pro implementaci metody zděděné z rozhraní a vrátí token této definici implementace metody.</span><span class="sxs-lookup"><span data-stu-id="92237-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92237-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92237-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (
    [in]  mdTypeDef         td,
    [in]  mdToken           tkBody,
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92237-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92237-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="92237-106">[v] Token `mdTypedef` implementující třídy.</span><span class="sxs-lookup"><span data-stu-id="92237-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="92237-107">[v] Nebo `mdMethodDef` `mdMemberRef` token textu kódu.</span><span class="sxs-lookup"><span data-stu-id="92237-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="92237-108">[v] Nebo `mdMethodDef` `mdMemberRef` token metody rozhraní, která je implementována.</span><span class="sxs-lookup"><span data-stu-id="92237-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92237-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="92237-109">Requirements</span></span>  
 <span data-ttu-id="92237-110">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92237-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92237-111">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="92237-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="92237-112">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="92237-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92237-113">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92237-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92237-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="92237-114">See also</span></span>

- [<span data-ttu-id="92237-115">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92237-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="92237-116">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92237-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
