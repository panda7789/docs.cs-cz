---
title: ASM_CACHE_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- ASM_CACHE_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_CACHE_FLAGS
helpviewer_keywords:
- ASM_CACHE_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 82e9a7da-321b-48b8-b239-52eaffda6be8
topic_type:
- apiref
ms.openlocfilehash: 85ac976daec8fd76ee21012a30611235609f4b34
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109495"
---
# <a name="asm_cache_flags-enumeration"></a><span data-ttu-id="8f828-102">ASM_CACHE_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="8f828-102">ASM_CACHE_FLAGS Enumeration</span></span>
<span data-ttu-id="8f828-103">Určuje zdroj sestavení, který je reprezentován [IAssemblyCacheItem](iassemblycacheitem-interface.md) v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="8f828-103">Indicates the source of an assembly that is represented by [IAssemblyCacheItem](iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f828-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f828-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="8f828-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8f828-105">Members</span></span>  
  
|<span data-ttu-id="8f828-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8f828-106">Member</span></span>|<span data-ttu-id="8f828-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8f828-107">Description</span></span>|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|<span data-ttu-id="8f828-108">Vytvoří výčet mezipaměti předkompilovaných sestavení pomocí nástroje Ngen. exe.</span><span class="sxs-lookup"><span data-stu-id="8f828-108">Enumerates the cache of precompiled assemblies by using Ngen.exe.</span></span>|  
|`ASM_CACHE_GAC`|<span data-ttu-id="8f828-109">Vytvoří výčet globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="8f828-109">Enumerates the global assembly cache.</span></span>|  
|`ASM_CACHE_DOWNLOAD`|<span data-ttu-id="8f828-110">Vytvoří výčet sestavení, která byla stažena na vyžádání nebo která byla Stínově zkopírována.</span><span class="sxs-lookup"><span data-stu-id="8f828-110">Enumerates the assemblies that have been downloaded on demand or that have been shadow-copied.</span></span>|  
|`ASM_CACHE_ROOT`|<span data-ttu-id="8f828-111">Označuje, že funkce [GetCachePath –](getcachepath-function.md) by měla vracet cestu k globální mezipaměti sestavení (Common Language Runtime) verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="8f828-111">Indicates that the [GetCachePath](getcachepath-function.md) function should return the path to the global assembly cache for the common language runtime (CLR) version 2.0.</span></span> <span data-ttu-id="8f828-112">Smysluplný pouze v kontextu volání [GetCachePath –](getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="8f828-112">Meaningful only in the context of a call to [GetCachePath](getcachepath-function.md).</span></span>|  
|`ASM_CACHE_ROOT_EX`|<span data-ttu-id="8f828-113">Označuje, že funkce [GetCachePath –](getcachepath-function.md) by měla vracet cestu k globální mezipaměti sestavení pro CLR verze 4.</span><span class="sxs-lookup"><span data-stu-id="8f828-113">Indicates that the [GetCachePath](getcachepath-function.md) function should return the path to the global assembly cache for CLR version 4.</span></span> <span data-ttu-id="8f828-114">Smysluplný pouze v kontextu volání [GetCachePath –](getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="8f828-114">Meaningful only in the context of a call to [GetCachePath](getcachepath-function.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8f828-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8f828-115">Requirements</span></span>  
 <span data-ttu-id="8f828-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f828-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f828-117">**Hlavička:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="8f828-117">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="8f828-118">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8f828-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8f828-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f828-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f828-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8f828-120">See also</span></span>

- [<span data-ttu-id="8f828-121">GetCachePath – funkce</span><span class="sxs-lookup"><span data-stu-id="8f828-121">GetCachePath Function</span></span>](getcachepath-function.md)
- [<span data-ttu-id="8f828-122">IAssemblyCacheItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f828-122">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
- [<span data-ttu-id="8f828-123">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="8f828-123">Fusion Enumerations</span></span>](fusion-enumerations.md)
