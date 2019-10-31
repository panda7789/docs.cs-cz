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
ms.openlocfilehash: 5a957a042875b546a18a17422f355b712756e91c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098172"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="0ae30-102">CorDebugHandleType – výčet</span><span class="sxs-lookup"><span data-stu-id="0ae30-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="0ae30-103">Určuje typ popisovače.</span><span class="sxs-lookup"><span data-stu-id="0ae30-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ae30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ae30-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="0ae30-105">Členové</span><span class="sxs-lookup"><span data-stu-id="0ae30-105">Members</span></span>  
  
|<span data-ttu-id="0ae30-106">Člen</span><span class="sxs-lookup"><span data-stu-id="0ae30-106">Member</span></span>|<span data-ttu-id="0ae30-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0ae30-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="0ae30-108">Popisovač je silný, což znemožňuje uvolnění objektu uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="0ae30-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="0ae30-109">Popisovač je slabý, což nebrání v uvolnění objektu uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="0ae30-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="0ae30-110">Popisovač se při shromáždění objektu nejedná.</span><span class="sxs-lookup"><span data-stu-id="0ae30-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0ae30-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ae30-111">Requirements</span></span>  
 <span data-ttu-id="0ae30-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ae30-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ae30-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0ae30-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ae30-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0ae30-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ae30-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ae30-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ae30-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ae30-116">See also</span></span>

- [<span data-ttu-id="0ae30-117">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="0ae30-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
