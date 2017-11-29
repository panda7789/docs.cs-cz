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
ms.openlocfilehash: 6042d5232995e68a4f59dfa68093446a03badfd6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="8c0a1-102">CorDebugNGenPolicy – výčet</span><span class="sxs-lookup"><span data-stu-id="8c0a1-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="8c0a1-103">Obsahuje hodnotu, která určuje, zda ladicí program načte nativní bitové kopie (NGen) z mezipaměť nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="8c0a1-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c0a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c0a1-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="8c0a1-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8c0a1-105">Members</span></span>  
  
|<span data-ttu-id="8c0a1-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="8c0a1-106">Member name</span></span>|<span data-ttu-id="8c0a1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8c0a1-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="8c0a1-108">V [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] aplikace, použijte bitových kopií z mezipaměti v místní nativních bitových kopií je zakázána.</span><span class="sxs-lookup"><span data-stu-id="8c0a1-108">In a [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="8c0a1-109">V aplikace na ploše toto nastavení nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="8c0a1-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c0a1-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c0a1-110">Remarks</span></span>  
 <span data-ttu-id="8c0a1-111">`CorDebugNGENPolicy` Výčet je používán [icordebugprocess5::enablengenpolicy –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="8c0a1-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="8c0a1-112">Zákaz použití bitové kopie z mezipaměti v místní nativních bitových kopií poskytuje pro ladění konzistentního prostředí tím, že zajistí, že ladicí program načte debuggable kompilována bitové kopie místo optimalizované nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="8c0a1-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c0a1-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c0a1-113">Requirements</span></span>  
 <span data-ttu-id="8c0a1-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c0a1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c0a1-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c0a1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c0a1-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c0a1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c0a1-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c0a1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c0a1-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c0a1-118">See Also</span></span>  
 [<span data-ttu-id="8c0a1-119">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="8c0a1-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
