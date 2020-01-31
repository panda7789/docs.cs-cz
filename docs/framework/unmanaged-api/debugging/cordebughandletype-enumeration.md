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
ms.openlocfilehash: 15572037940f7c45ec5dcb7e34599756e15fd3bd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793914"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="7d2ed-102">CorDebugHandleType – výčet</span><span class="sxs-lookup"><span data-stu-id="7d2ed-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="7d2ed-103">Určuje typ popisovače.</span><span class="sxs-lookup"><span data-stu-id="7d2ed-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d2ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d2ed-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="7d2ed-105">Členové</span><span class="sxs-lookup"><span data-stu-id="7d2ed-105">Members</span></span>  
  
|<span data-ttu-id="7d2ed-106">Člen</span><span class="sxs-lookup"><span data-stu-id="7d2ed-106">Member</span></span>|<span data-ttu-id="7d2ed-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7d2ed-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="7d2ed-108">Popisovač je silný, což znemožňuje uvolnění objektu uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="7d2ed-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="7d2ed-109">Popisovač je slabý, což nebrání v uvolnění objektu uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="7d2ed-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="7d2ed-110">Popisovač se při shromáždění objektu nejedná.</span><span class="sxs-lookup"><span data-stu-id="7d2ed-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7d2ed-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d2ed-111">Requirements</span></span>  
 <span data-ttu-id="7d2ed-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d2ed-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d2ed-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7d2ed-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d2ed-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7d2ed-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d2ed-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d2ed-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d2ed-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d2ed-116">See also</span></span>

- [<span data-ttu-id="7d2ed-117">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="7d2ed-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
