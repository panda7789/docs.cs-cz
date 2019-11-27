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
ms.openlocfilehash: a73afaebc2943190eeeee50367ecd31f1fb59df1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432449"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="6037c-102">IMetaDataEmit::SetParent – metoda</span><span class="sxs-lookup"><span data-stu-id="6037c-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="6037c-103">Stanoví, že zadaný člen, jak je definován předchozím voláním [IMetaDataEmit::D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), je členem zadaného typu, jak je definováno předchozím voláním [IMetaDataEmit::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="6037c-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6037c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6037c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParent (   
    [in]  mdMemberRef mr,   
    [in]  mdToken     tk   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6037c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6037c-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="6037c-106">pro Token `mdMemberRef` pro příjem nového nadřazeného prvku.</span><span class="sxs-lookup"><span data-stu-id="6037c-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="6037c-107">pro `mdToken` pro novou nadřazenou položku.</span><span class="sxs-lookup"><span data-stu-id="6037c-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6037c-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6037c-108">Requirements</span></span>  
 <span data-ttu-id="6037c-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6037c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6037c-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6037c-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6037c-111">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="6037c-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6037c-112">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6037c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6037c-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6037c-113">See also</span></span>

- [<span data-ttu-id="6037c-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6037c-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6037c-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6037c-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
