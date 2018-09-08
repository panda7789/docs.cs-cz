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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b712c6ae5978e83dab085f48dd1fd572757384a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44197757"
---
# <a name="asmcacheflags-enumeration"></a><span data-ttu-id="8d5fa-102">ASM_CACHE_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="8d5fa-102">ASM_CACHE_FLAGS Enumeration</span></span>
<span data-ttu-id="8d5fa-103">Určuje zdroj sestavení, která je reprezentována [iassemblycacheitem –](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="8d5fa-103">Indicates the source of an assembly that is represented by [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d5fa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d5fa-104">Syntax</span></span>  
  
```  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="8d5fa-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8d5fa-105">Members</span></span>  
  
|<span data-ttu-id="8d5fa-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8d5fa-106">Member</span></span>|<span data-ttu-id="8d5fa-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8d5fa-107">Description</span></span>|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|<span data-ttu-id="8d5fa-108">Vytvoří výčet mezipaměti předkompilovaných sestavení pomocí Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="8d5fa-108">Enumerates the cache of precompiled assemblies by using Ngen.exe.</span></span>|  
|`ASM_CACHE_GAC`|<span data-ttu-id="8d5fa-109">Vytvoří výčet globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="8d5fa-109">Enumerates the global assembly cache.</span></span>|  
|`ASM_CACHE_DOWNLOAD`|<span data-ttu-id="8d5fa-110">Vytvoří výčet sestavení, které byly staženy na vyžádání nebo která byla vytvořena stínová kopie.</span><span class="sxs-lookup"><span data-stu-id="8d5fa-110">Enumerates the assemblies that have been downloaded on demand or that have been shadow-copied.</span></span>|  
|`ASM_CACHE_ROOT`|<span data-ttu-id="8d5fa-111">Označuje, že [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) funkce by měla vrátit cestu k mezipaměti globálního sestavení pro modul common language runtime (CLR) verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="8d5fa-111">Indicates that the [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) function should return the path to the global assembly cache for the common language runtime (CLR) version 2.0.</span></span> <span data-ttu-id="8d5fa-112">Smysl pouze v kontextu volání [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="8d5fa-112">Meaningful only in the context of a call to [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span></span>|  
|`ASM_CACHE_ROOT_EX`|<span data-ttu-id="8d5fa-113">Označuje, že [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) funkce by měla vrátit cestu do globální mezipaměti sestavení pro modul CLR verze 4.</span><span class="sxs-lookup"><span data-stu-id="8d5fa-113">Indicates that the [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) function should return the path to the global assembly cache for CLR version 4.</span></span> <span data-ttu-id="8d5fa-114">Smysl pouze v kontextu volání [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="8d5fa-114">Meaningful only in the context of a call to [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8d5fa-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d5fa-115">Requirements</span></span>  
 <span data-ttu-id="8d5fa-116">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d5fa-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d5fa-117">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="8d5fa-117">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="8d5fa-118">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8d5fa-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8d5fa-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d5fa-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d5fa-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d5fa-120">See Also</span></span>  
 [<span data-ttu-id="8d5fa-121">GetCachePath – funkce</span><span class="sxs-lookup"><span data-stu-id="8d5fa-121">GetCachePath Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 [<span data-ttu-id="8d5fa-122">IAssemblyCacheItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d5fa-122">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)  
 [<span data-ttu-id="8d5fa-123">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="8d5fa-123">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
