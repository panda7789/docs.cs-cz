---
title: CorDebugNGenPolicy – výčet
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugNGenPolicy
helpviewer_keywords:
- CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc5a06e6b3cc1e9338d860cdb110bf7d516080be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404021"
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="ba882-102">CorDebugNGenPolicy – výčet</span><span class="sxs-lookup"><span data-stu-id="ba882-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="ba882-103">Obsahuje hodnotu, která určuje, zda ladicí program načte nativní bitové kopie (NGen) z mezipaměť nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="ba882-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba882-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba882-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="ba882-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ba882-105">Members</span></span>  
  
|<span data-ttu-id="ba882-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="ba882-106">Member name</span></span>|<span data-ttu-id="ba882-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ba882-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="ba882-108">V [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] aplikace, použijte bitových kopií z mezipaměti v místní nativních bitových kopií je zakázána.</span><span class="sxs-lookup"><span data-stu-id="ba882-108">In a [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="ba882-109">V aplikace na ploše toto nastavení nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="ba882-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba882-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ba882-110">Remarks</span></span>  
 <span data-ttu-id="ba882-111">`CorDebugNGENPolicy` Výčet je používán [icordebugprocess5::enablengenpolicy –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="ba882-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="ba882-112">Zákaz použití bitové kopie z mezipaměti v místní nativních bitových kopií poskytuje pro ladění konzistentního prostředí tím, že zajistí, že ladicí program načte debuggable kompilována bitové kopie místo optimalizované nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="ba882-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba882-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ba882-113">Requirements</span></span>  
 <span data-ttu-id="ba882-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba882-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba882-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba882-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba882-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba882-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba882-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba882-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba882-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba882-118">See Also</span></span>  
 [<span data-ttu-id="ba882-119">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="ba882-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
