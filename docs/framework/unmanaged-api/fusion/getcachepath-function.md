---
title: GetCachePath – funkce
ms.date: 03/30/2017
api_name:
- GetCachePath
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- GetCachePath
helpviewer_keywords:
- GetCachePath function [.NET Framework fusion]
ms.assetid: d977ad29-6619-42e1-b0be-bc25ea950e80
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc29c5f975424e3dbe91e206f6a05f830d760398
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472648"
---
# <a name="getcachepath-function"></a><span data-ttu-id="84c75-102">GetCachePath – funkce</span><span class="sxs-lookup"><span data-stu-id="84c75-102">GetCachePath Function</span></span>
<span data-ttu-id="84c75-103">Získá cestu k sestavení v mezipaměti, pomocí zadané příznaky.</span><span class="sxs-lookup"><span data-stu-id="84c75-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84c75-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84c75-104">Syntax</span></span>  
  
```  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="84c75-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84c75-105">Parameters</span></span>  
 `dwCacheFlags`  
 <span data-ttu-id="84c75-106">[in] [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) hodnotu, která určuje zdroj sestavení v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="84c75-106">[in] An [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="84c75-107">[out] Vrácený ukazatel na cestu.</span><span class="sxs-lookup"><span data-stu-id="84c75-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="84c75-108">[out v] Požadovaná maximální délce `pwzCachePath`a po návratu, skutečná délka `pwzCachePath`.</span><span class="sxs-lookup"><span data-stu-id="84c75-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84c75-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="84c75-109">Requirements</span></span>  
 <span data-ttu-id="84c75-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84c75-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84c75-111">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="84c75-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="84c75-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84c75-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84c75-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84c75-113">See also</span></span>
- [<span data-ttu-id="84c75-114">ASM_CACHE_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="84c75-114">ASM_CACHE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)
- [<span data-ttu-id="84c75-115">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="84c75-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
