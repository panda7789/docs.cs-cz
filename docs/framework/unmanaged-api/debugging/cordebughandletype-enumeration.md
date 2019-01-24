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
ms.openlocfilehash: 5ca7508c675ccc4c4ee0c07a2d7790bb5de7a668
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594587"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="9791e-102">CorDebugHandleType – výčet</span><span class="sxs-lookup"><span data-stu-id="9791e-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="9791e-103">Určuje typ popisovače.</span><span class="sxs-lookup"><span data-stu-id="9791e-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9791e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9791e-104">Syntax</span></span>  
  
```  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="9791e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="9791e-105">Members</span></span>  
  
|<span data-ttu-id="9791e-106">Člen</span><span class="sxs-lookup"><span data-stu-id="9791e-106">Member</span></span>|<span data-ttu-id="9791e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9791e-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="9791e-108">Popisovač je silný, která zabraňuje objektu je vyžádá zpět systém uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9791e-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="9791e-109">Popisovač je slabé, který nebrání objektu je vyžádá zpět systém uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9791e-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="9791e-110">Když objekt se shromažďují se stanou neplatnými popisovač.</span><span class="sxs-lookup"><span data-stu-id="9791e-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9791e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9791e-111">Requirements</span></span>  
 <span data-ttu-id="9791e-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9791e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9791e-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9791e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9791e-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9791e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9791e-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9791e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9791e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9791e-116">See also</span></span>
- [<span data-ttu-id="9791e-117">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="9791e-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
