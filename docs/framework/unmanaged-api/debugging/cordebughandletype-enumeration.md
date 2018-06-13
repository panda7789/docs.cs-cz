---
title: CorDebugHandleType – výčet
ms.date: 03/30/2017
api_name:
- CorDebugHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugHandleType
helpviewer_keywords:
- CorDebugHandleType enumeration [.NET Framework debugging]
ms.assetid: 84296b55-c2c5-424c-ac9c-8e28e2895945
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2898f530fe3f9368778d0f854e8254f7b32d5293
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404934"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="f1de2-102">CorDebugHandleType – výčet</span><span class="sxs-lookup"><span data-stu-id="f1de2-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="f1de2-103">Určuje typ popisovače.</span><span class="sxs-lookup"><span data-stu-id="f1de2-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1de2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1de2-104">Syntax</span></span>  
  
```  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="f1de2-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f1de2-105">Members</span></span>  
  
|<span data-ttu-id="f1de2-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f1de2-106">Member</span></span>|<span data-ttu-id="f1de2-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f1de2-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="f1de2-108">Popisovač je silné, aby se zabránilo objekt převzata systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f1de2-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="f1de2-109">Popisovač je slabé, který nezabrání objekt převzata systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f1de2-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="f1de2-110">Když jsou shromažďována objekt stane neplatný popisovač.</span><span class="sxs-lookup"><span data-stu-id="f1de2-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f1de2-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f1de2-111">Requirements</span></span>  
 <span data-ttu-id="f1de2-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1de2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1de2-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1de2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1de2-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1de2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1de2-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1de2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1de2-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1de2-116">See Also</span></span>  
 [<span data-ttu-id="f1de2-117">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="f1de2-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
