---
title: "GetCachePath – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetCachePath
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: GetCachePath
helpviewer_keywords: GetCachePath function [.NET Framework fusion]
ms.assetid: d977ad29-6619-42e1-b0be-bc25ea950e80
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 924482bf34d53d3d7144c4bae93a00a8f8d2ad4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="getcachepath-function"></a><span data-ttu-id="c65a6-102">GetCachePath – funkce</span><span class="sxs-lookup"><span data-stu-id="c65a6-102">GetCachePath Function</span></span>
<span data-ttu-id="c65a6-103">Získá cestu k sestavení v mezipaměti, pomocí zadané příznaky.</span><span class="sxs-lookup"><span data-stu-id="c65a6-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c65a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c65a6-104">Syntax</span></span>  
  
```  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c65a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c65a6-105">Parameters</span></span>  
 `dwCacheFlags`  
 <span data-ttu-id="c65a6-106">[v] [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) hodnotu, která určuje zdroj v mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="c65a6-106">[in] An [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="c65a6-107">[out] Vrácený ukazatel na cestu.</span><span class="sxs-lookup"><span data-stu-id="c65a6-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="c65a6-108">[ve out] Požadovaný maximální délku `pwzCachePath`a po návratu, skutečná délka `pwzCachePath`.</span><span class="sxs-lookup"><span data-stu-id="c65a6-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c65a6-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c65a6-109">Requirements</span></span>  
 <span data-ttu-id="c65a6-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c65a6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c65a6-111">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="c65a6-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c65a6-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c65a6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c65a6-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c65a6-113">See Also</span></span>  
 [<span data-ttu-id="c65a6-114">ASM_CACHE_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="c65a6-114">ASM_CACHE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)  
 [<span data-ttu-id="c65a6-115">Fúze globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="c65a6-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
