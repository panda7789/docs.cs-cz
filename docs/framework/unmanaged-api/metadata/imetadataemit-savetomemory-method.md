---
title: "IMetaDataEmit::SaveToMemory – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SaveToMemory
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SaveToMemory
helpviewer_keywords:
- IMetaDataEmit::SaveToMemory method [.NET Framework metadata]
- SaveToMemory method [.NET Framework metadata]
ms.assetid: d5237628-2675-45ed-a39e-65c0731b6a56
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 685ed69964970f505ad6f938af361c48664d2279
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="46cbb-102">IMetaDataEmit::SaveToMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="46cbb-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="46cbb-103">Uloží všechna metadata v aktuálním oboru do určené oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="46cbb-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46cbb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46cbb-104">Syntax</span></span>  
  
```  
HRESULT SaveToMemory (   
    [out]  void        *pbData,   
    [in]   ULONG       cbData   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="46cbb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="46cbb-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="46cbb-106">[out] Adresa, kam chcete zahájit zápis metadat.</span><span class="sxs-lookup"><span data-stu-id="46cbb-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="46cbb-107">[v] Velikost v bajtech, přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="46cbb-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46cbb-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="46cbb-108">Requirements</span></span>  
 <span data-ttu-id="46cbb-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46cbb-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46cbb-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="46cbb-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="46cbb-111">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="46cbb-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="46cbb-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46cbb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46cbb-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="46cbb-113">See Also</span></span>  
 [<span data-ttu-id="46cbb-114">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46cbb-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="46cbb-115">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46cbb-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
