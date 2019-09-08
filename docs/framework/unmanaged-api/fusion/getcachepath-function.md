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
ms.openlocfilehash: b1c28f32a4b24393483241bd2d7d6f550b8b65ba
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796905"
---
# <a name="getcachepath-function"></a><span data-ttu-id="cd189-102">GetCachePath – funkce</span><span class="sxs-lookup"><span data-stu-id="cd189-102">GetCachePath Function</span></span>
<span data-ttu-id="cd189-103">Načte cestu k sestavení v mezipaměti pomocí zadaných příznaků.</span><span class="sxs-lookup"><span data-stu-id="cd189-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd189-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd189-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd189-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd189-105">Parameters</span></span>  
 `dwCacheFlags`  
 <span data-ttu-id="cd189-106">pro Hodnota [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) , která označuje zdroj sestavení v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="cd189-106">[in] An [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="cd189-107">mimo Vrácený ukazatel na cestu.</span><span class="sxs-lookup"><span data-stu-id="cd189-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="cd189-108">[in, out] Požadovaná maximální délka `pwzCachePath`a po návratu, skutečná `pwzCachePath`délka.</span><span class="sxs-lookup"><span data-stu-id="cd189-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd189-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cd189-109">Requirements</span></span>  
 <span data-ttu-id="cd189-110">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd189-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd189-111">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="cd189-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="cd189-112">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd189-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd189-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd189-113">See also</span></span>

- [<span data-ttu-id="cd189-114">ASM_CACHE_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="cd189-114">ASM_CACHE_FLAGS Enumeration</span></span>](asm-cache-flags-enumeration.md)
- [<span data-ttu-id="cd189-115">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="cd189-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
