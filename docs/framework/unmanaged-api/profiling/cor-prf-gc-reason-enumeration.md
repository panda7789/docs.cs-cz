---
title: COR_PRF_GC_REASON – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_REASON
helpviewer_keywords:
- COR_PRF_GC_REASON enumeration [.NET Framework profiling]
ms.assetid: 72822b95-a7fb-485e-9d55-1cb016d9a458
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4f5a596608719889e6440e5cd42dafb82abaa074
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753722"
---
# <a name="corprfgcreason-enumeration"></a><span data-ttu-id="163aa-102">COR_PRF_GC_REASON – výčet</span><span class="sxs-lookup"><span data-stu-id="163aa-102">COR_PRF_GC_REASON Enumeration</span></span>
<span data-ttu-id="163aa-103">Označuje, že uvolňování paměti dochází důvod.</span><span class="sxs-lookup"><span data-stu-id="163aa-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="163aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="163aa-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="163aa-105">Členové</span><span class="sxs-lookup"><span data-stu-id="163aa-105">Members</span></span>  
  
|<span data-ttu-id="163aa-106">Člen</span><span class="sxs-lookup"><span data-stu-id="163aa-106">Member</span></span>|<span data-ttu-id="163aa-107">Popis</span><span class="sxs-lookup"><span data-stu-id="163aa-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="163aa-108">Kolekce paměti byla vyvolaná <xref:System.GC.Collect%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="163aa-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="163aa-109">Důvod není zadána.</span><span class="sxs-lookup"><span data-stu-id="163aa-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="163aa-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="163aa-110">Requirements</span></span>  
 <span data-ttu-id="163aa-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="163aa-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="163aa-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="163aa-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="163aa-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="163aa-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="163aa-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="163aa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="163aa-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="163aa-115">See also</span></span>

- [<span data-ttu-id="163aa-116">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="163aa-116">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
