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
ms.openlocfilehash: 05b2530bde2f4532e94610a683e7bbc2f59540aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178383"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="95f8e-102">IMetaDataEmit::DefineMethodImpl – metoda</span><span class="sxs-lookup"><span data-stu-id="95f8e-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="95f8e-103">Vytvoří definici pro implementaci metody zděděné z rozhraní a vrátí token k definici této implementace metody.</span><span class="sxs-lookup"><span data-stu-id="95f8e-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95f8e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95f8e-104">Syntax</span></span>  
  
```  
HRESULT DefineMethodImpl (   
    [in]  mdTypeDef         td,   
    [in]  mdToken           tkBody,   
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95f8e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="95f8e-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="95f8e-106">[in] `mdTypedef` Token implementující třídu.</span><span class="sxs-lookup"><span data-stu-id="95f8e-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="95f8e-107">[in] `mdMethodDef` Nebo `mdMethodRef` token těla kódu.</span><span class="sxs-lookup"><span data-stu-id="95f8e-107">[in] The `mdMethodDef` or `mdMethodRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="95f8e-108">[in] `mdMethodDef` Nebo `mdMethodRef` token metody rozhraní se implementuje.</span><span class="sxs-lookup"><span data-stu-id="95f8e-108">[in] The `mdMethodDef` or `mdMethodRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95f8e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="95f8e-109">Requirements</span></span>  
 <span data-ttu-id="95f8e-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95f8e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95f8e-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="95f8e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="95f8e-112">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="95f8e-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="95f8e-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="95f8e-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="95f8e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95f8e-114">See also</span></span>

- [<span data-ttu-id="95f8e-115">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95f8e-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="95f8e-116">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95f8e-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
