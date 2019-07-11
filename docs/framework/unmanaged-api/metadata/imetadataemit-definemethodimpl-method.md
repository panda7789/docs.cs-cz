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
ms.openlocfilehash: b64275def01d7b62f9a461de69a286769094305e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777594"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="6e746-102">IMetaDataEmit::DefineMethodImpl – metoda</span><span class="sxs-lookup"><span data-stu-id="6e746-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="6e746-103">Vytvoří definici pro implementaci metody zděděné z rozhraní a vrátí token k definici této implementace metody.</span><span class="sxs-lookup"><span data-stu-id="6e746-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e746-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e746-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (   
    [in]  mdTypeDef         td,   
    [in]  mdToken           tkBody,   
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e746-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e746-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="6e746-106">[in] `mdTypedef` Token implementující třídu.</span><span class="sxs-lookup"><span data-stu-id="6e746-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="6e746-107">[in] `mdMethodDef` Nebo `mdMemberRef` token těla kódu.</span><span class="sxs-lookup"><span data-stu-id="6e746-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="6e746-108">[in] `mdMethodDef` Nebo `mdMemberRef` token metody rozhraní se implementuje.</span><span class="sxs-lookup"><span data-stu-id="6e746-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e746-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6e746-109">Requirements</span></span>  
 <span data-ttu-id="6e746-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e746-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e746-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6e746-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6e746-112">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6e746-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e746-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e746-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e746-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e746-114">See also</span></span>

- [<span data-ttu-id="6e746-115">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e746-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6e746-116">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e746-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
