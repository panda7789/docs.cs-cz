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
ms.openlocfilehash: 7389e9233fd946cdb2c810bec01cfbfffc8b707d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175600"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="c3ca2-102">IMetaDataEmit::SetParent – metoda</span><span class="sxs-lookup"><span data-stu-id="c3ca2-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="c3ca2-103">Stanoví, že zadaný člen, jak je definován předchozí volání [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), je členem zadaného typu, jak je definováno předchozí volání [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="c3ca2-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3ca2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3ca2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParent (
    [in]  mdMemberRef mr,
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3ca2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3ca2-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="c3ca2-106">[v] Token `mdMemberRef` pro příjem nového nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="c3ca2-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="c3ca2-107">[v] Pro `mdToken` nového rodiče.</span><span class="sxs-lookup"><span data-stu-id="c3ca2-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3ca2-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c3ca2-108">Requirements</span></span>  
 <span data-ttu-id="c3ca2-109">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3ca2-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3ca2-110">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="c3ca2-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c3ca2-111">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c3ca2-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3ca2-112">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3ca2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3ca2-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3ca2-113">See also</span></span>

- [<span data-ttu-id="c3ca2-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3ca2-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c3ca2-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3ca2-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
