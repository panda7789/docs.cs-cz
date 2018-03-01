---
title: "IMetaDataEmit::SetMethodImplFlags – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8026ec666e853b5a0ccd98e5ba75a3e04ffea9a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="993f2-102">IMetaDataEmit::SetMethodImplFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="993f2-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="993f2-103">Nastaví nebo aktualizuje podpis metadata implementace zděděné metody, který odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="993f2-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="993f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="993f2-104">Syntax</span></span>  
  
```  
HRESULT SetMethodImplFlags (   
    [in]  mdMethodDef   md,   
    [in]  DWORD         dwImplFlags   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="993f2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="993f2-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="993f2-106">[v] Token pro metodu změnit.</span><span class="sxs-lookup"><span data-stu-id="993f2-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="993f2-107">[v] Kombinace hodnot [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) výčet, který určuje funkce, které metoda implementace.</span><span class="sxs-lookup"><span data-stu-id="993f2-107">[in] A combination of the values of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="993f2-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="993f2-108">Requirements</span></span>  
 <span data-ttu-id="993f2-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="993f2-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="993f2-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="993f2-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="993f2-111">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="993f2-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="993f2-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="993f2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="993f2-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="993f2-113">See Also</span></span>  
 [<span data-ttu-id="993f2-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="993f2-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="993f2-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="993f2-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
