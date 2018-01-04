---
title: "CorDebugNGenPolicy – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: CorDebugNGenPolicy
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugNGenPolicy
helpviewer_keywords: CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 89767da7178319ed1add3dda0620062893487bfd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="aa5ff-102">CorDebugNGenPolicy – výčet</span><span class="sxs-lookup"><span data-stu-id="aa5ff-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="aa5ff-103">Obsahuje hodnotu, která určuje, zda ladicí program načte nativní bitové kopie (NGen) z mezipaměť nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="aa5ff-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa5ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa5ff-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="aa5ff-105">Členové</span><span class="sxs-lookup"><span data-stu-id="aa5ff-105">Members</span></span>  
  
|<span data-ttu-id="aa5ff-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="aa5ff-106">Member name</span></span>|<span data-ttu-id="aa5ff-107">Popis</span><span class="sxs-lookup"><span data-stu-id="aa5ff-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="aa5ff-108">V [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] aplikace, použijte bitových kopií z mezipaměti v místní nativních bitových kopií je zakázána.</span><span class="sxs-lookup"><span data-stu-id="aa5ff-108">In a [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="aa5ff-109">V aplikace na ploše toto nastavení nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="aa5ff-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa5ff-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aa5ff-110">Remarks</span></span>  
 <span data-ttu-id="aa5ff-111">`CorDebugNGENPolicy` Výčet je používán [icordebugprocess5::enablengenpolicy –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="aa5ff-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="aa5ff-112">Zákaz použití bitové kopie z mezipaměti v místní nativních bitových kopií poskytuje pro ladění konzistentního prostředí tím, že zajistí, že ladicí program načte debuggable kompilována bitové kopie místo optimalizované nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="aa5ff-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa5ff-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aa5ff-113">Requirements</span></span>  
 <span data-ttu-id="aa5ff-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa5ff-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa5ff-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa5ff-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa5ff-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa5ff-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa5ff-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa5ff-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa5ff-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa5ff-118">See Also</span></span>  
 [<span data-ttu-id="aa5ff-119">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="aa5ff-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
