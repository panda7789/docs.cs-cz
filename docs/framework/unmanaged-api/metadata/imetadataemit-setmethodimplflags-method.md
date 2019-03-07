---
title: IMetaDataEmit::SetMethodImplFlags – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodImplFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodImplFlags
helpviewer_keywords:
- IMetaDataEmit::SetMethodImplFlags method [.NET Framework metadata]
- SetMethodImpFlags method [.NET Framework metadata]
ms.assetid: 4bc82d9b-9544-4be3-ba51-a2d4d806158a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98df83569681dab5a7aa15651181373ee5d559dc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479204"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="e6d73-102">IMetaDataEmit::SetMethodImplFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="e6d73-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="e6d73-103">Nastaví nebo aktualizuje podpis metadat implementace zděděné metody, na který odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="e6d73-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6d73-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6d73-104">Syntax</span></span>  
  
```  
HRESULT SetMethodImplFlags (   
    [in]  mdMethodDef   md,   
    [in]  DWORD         dwImplFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6d73-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e6d73-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="e6d73-106">[in] Token metody změnit.</span><span class="sxs-lookup"><span data-stu-id="e6d73-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="e6d73-107">[in] Kombinace hodnot [cormethodimpl –](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) výčet, který určuje funkce implementace metody.</span><span class="sxs-lookup"><span data-stu-id="e6d73-107">[in] A combination of the values of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6d73-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e6d73-108">Requirements</span></span>  
 <span data-ttu-id="e6d73-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6d73-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6d73-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e6d73-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e6d73-111">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e6d73-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e6d73-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6d73-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6d73-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6d73-113">See also</span></span>
- [<span data-ttu-id="e6d73-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e6d73-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e6d73-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e6d73-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
