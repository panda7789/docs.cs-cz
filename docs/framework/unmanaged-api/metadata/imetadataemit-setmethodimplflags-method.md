---
title: "IMetaDataEmit::SetMethodImplFlags – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetMethodImplFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetMethodImplFlags
helpviewer_keywords:
- IMetaDataEmit::SetMethodImplFlags method [.NET Framework metadata]
- SetMethodImpFlags method [.NET Framework metadata]
ms.assetid: 4bc82d9b-9544-4be3-ba51-a2d4d806158a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d69940d5cffe397d009b7364a20a09dbbd95db4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="b7956-102">IMetaDataEmit::SetMethodImplFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="b7956-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="b7956-103">Nastaví nebo aktualizuje podpis metadata implementace zděděné metody, který odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="b7956-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7956-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7956-104">Syntax</span></span>  
  
```  
HRESULT SetMethodImplFlags (   
    [in]  mdMethodDef   md,   
    [in]  DWORD         dwImplFlags   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7956-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7956-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="b7956-106">[v] Token pro metodu změnit.</span><span class="sxs-lookup"><span data-stu-id="b7956-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="b7956-107">[v] Kombinace hodnot [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) výčet, který určuje funkce, které metoda implementace.</span><span class="sxs-lookup"><span data-stu-id="b7956-107">[in] A combination of the values of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7956-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7956-108">Requirements</span></span>  
 <span data-ttu-id="b7956-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7956-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7956-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b7956-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b7956-111">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b7956-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7956-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7956-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7956-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7956-113">See Also</span></span>  
 [<span data-ttu-id="b7956-114">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7956-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="b7956-115">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7956-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
