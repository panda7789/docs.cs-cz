---
title: "IMetaDataEmit::DefineMethodImpl – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineMethodImpl
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineMethodImpl
helpviewer_keywords:
- DefineMethodImpl method [.NET Framework metadata]
- IMetaDataEmit::DefineMethodImpl method [.NET Framework metadata]
ms.assetid: 9dcc8b3d-33ee-4c7c-8d6f-322c57b94a0f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 126cf950b71ed2325006b14927ae95517f7c6dc6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="689bd-102">IMetaDataEmit::DefineMethodImpl – metoda</span><span class="sxs-lookup"><span data-stu-id="689bd-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="689bd-103">Vytvoří definici implementace metody zděděno z rozhraní a vrátí token tuto definici implementace metod.</span><span class="sxs-lookup"><span data-stu-id="689bd-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="689bd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="689bd-104">Syntax</span></span>  
  
```  
HRESULT DefineMethodImpl (   
    [in]  mdTypeDef         td,   
    [in]  mdToken           tkBody,   
    [in]  mdToken           tkDecl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="689bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="689bd-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="689bd-106">[v] `mdTypedef` Tokenu z implementující třídu.</span><span class="sxs-lookup"><span data-stu-id="689bd-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="689bd-107">[v] `mdMethodDef` Nebo `mdMethodRef` těla kód tokenu.</span><span class="sxs-lookup"><span data-stu-id="689bd-107">[in] The `mdMethodDef` or `mdMethodRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="689bd-108">[v] `mdMethodDef` Nebo `mdMethodRef` tokenu z se implementuje metodu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="689bd-108">[in] The `mdMethodDef` or `mdMethodRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="689bd-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="689bd-109">Requirements</span></span>  
 <span data-ttu-id="689bd-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="689bd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="689bd-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="689bd-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="689bd-112">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="689bd-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="689bd-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="689bd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="689bd-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="689bd-114">See Also</span></span>  
 [<span data-ttu-id="689bd-115">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="689bd-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="689bd-116">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="689bd-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
