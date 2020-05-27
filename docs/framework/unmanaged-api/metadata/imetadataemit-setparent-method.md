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
ms.openlocfilehash: da82950ea1a0da81c77d173be9ab45dcb3001bfe
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007829"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="823bd-102">IMetaDataEmit::SetParent – metoda</span><span class="sxs-lookup"><span data-stu-id="823bd-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="823bd-103">Stanoví, že zadaný člen, jak je definován předchozím voláním [IMetaDataEmit::D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), je členem zadaného typu, jak je definováno předchozím voláním [IMetaDataEmit::D efinetypedef](imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="823bd-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="823bd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="823bd-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParent (
    [in]  mdMemberRef mr,
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="823bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="823bd-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="823bd-106">pro `mdMemberRef`Token pro příjem nového nadřazeného prvku</span><span class="sxs-lookup"><span data-stu-id="823bd-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="823bd-107">pro `mdToken`Pro novou nadřazenou položku.</span><span class="sxs-lookup"><span data-stu-id="823bd-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="823bd-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="823bd-108">Requirements</span></span>  
 <span data-ttu-id="823bd-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="823bd-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="823bd-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="823bd-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="823bd-111">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="823bd-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="823bd-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="823bd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="823bd-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="823bd-113">See also</span></span>

- [<span data-ttu-id="823bd-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="823bd-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="823bd-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="823bd-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
