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
ms.openlocfilehash: f6f5cd47abd4c17021bc324898a096ff70a3db2e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739989"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="ceb9c-102">CorDebugHandleType – výčet</span><span class="sxs-lookup"><span data-stu-id="ceb9c-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="ceb9c-103">Určuje typ popisovače.</span><span class="sxs-lookup"><span data-stu-id="ceb9c-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceb9c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ceb9c-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="ceb9c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ceb9c-105">Members</span></span>  
  
|<span data-ttu-id="ceb9c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="ceb9c-106">Member</span></span>|<span data-ttu-id="ceb9c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ceb9c-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="ceb9c-108">Popisovač je silný, která zabraňuje objektu je vyžádá zpět systém uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ceb9c-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="ceb9c-109">Popisovač je slabé, který nebrání objektu je vyžádá zpět systém uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ceb9c-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="ceb9c-110">Když objekt se shromažďují se stanou neplatnými popisovač.</span><span class="sxs-lookup"><span data-stu-id="ceb9c-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ceb9c-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ceb9c-111">Requirements</span></span>  
 <span data-ttu-id="ceb9c-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ceb9c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ceb9c-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ceb9c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ceb9c-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ceb9c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ceb9c-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ceb9c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceb9c-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ceb9c-116">See also</span></span>

- [<span data-ttu-id="ceb9c-117">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="ceb9c-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
