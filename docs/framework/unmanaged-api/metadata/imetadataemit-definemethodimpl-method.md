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
ms.openlocfilehash: 5ed5afbbf49b6680d00e78b6af3d45c6f0a7229d
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004488"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="e8363-102">IMetaDataEmit::DefineMethodImpl – metoda</span><span class="sxs-lookup"><span data-stu-id="e8363-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="e8363-103">Vytvoří definici pro implementaci metody zděděné z rozhraní a vrátí token této metody – definice implementace.</span><span class="sxs-lookup"><span data-stu-id="e8363-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8363-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8363-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (
    [in]  mdTypeDef         td,
    [in]  mdToken           tkBody,
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8363-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8363-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="e8363-106">pro `mdTypedef`Token implementující třídy.</span><span class="sxs-lookup"><span data-stu-id="e8363-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="e8363-107">pro `mdMethodDef`Token nebo pro `mdMemberRef` tělo kódu.</span><span class="sxs-lookup"><span data-stu-id="e8363-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="e8363-108">pro `mdMethodDef`Token nebo pro `mdMemberRef` implementovanou metodu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e8363-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8363-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e8363-109">Requirements</span></span>  
 <span data-ttu-id="e8363-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8363-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8363-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e8363-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e8363-112">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="e8363-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8363-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8363-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8363-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8363-114">See also</span></span>

- [<span data-ttu-id="e8363-115">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e8363-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="e8363-116">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e8363-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
