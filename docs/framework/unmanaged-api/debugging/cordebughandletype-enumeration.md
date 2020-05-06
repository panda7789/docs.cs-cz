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
ms.openlocfilehash: 2d296c1778e00c4c72e860e0705994518d1481e8
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795877"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="aa86a-102">CorDebugHandleType – výčet</span><span class="sxs-lookup"><span data-stu-id="aa86a-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="aa86a-103">Určuje typ popisovače.</span><span class="sxs-lookup"><span data-stu-id="aa86a-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa86a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa86a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="aa86a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="aa86a-105">Members</span></span>  
  
|<span data-ttu-id="aa86a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="aa86a-106">Member</span></span>|<span data-ttu-id="aa86a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="aa86a-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="aa86a-108">Popisovač je silný, což znemožňuje uvolnění objektu uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="aa86a-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="aa86a-109">Popisovač je slabý, což nebrání v uvolnění objektu uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="aa86a-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="aa86a-110">Popisovač se při shromáždění objektu nejedná.</span><span class="sxs-lookup"><span data-stu-id="aa86a-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aa86a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aa86a-111">Requirements</span></span>  
 <span data-ttu-id="aa86a-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa86a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa86a-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="aa86a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa86a-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="aa86a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa86a-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa86a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa86a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa86a-116">See also</span></span>

- [<span data-ttu-id="aa86a-117">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="aa86a-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
