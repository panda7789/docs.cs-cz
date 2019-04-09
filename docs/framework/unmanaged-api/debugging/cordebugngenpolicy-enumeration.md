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
ms.openlocfilehash: ca922d8b582c0608073d4fd0ba986167ae470e34
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109665"
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="e65e9-102">CorDebugNGenPolicy – výčet</span><span class="sxs-lookup"><span data-stu-id="e65e9-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="e65e9-103">Poskytuje hodnotu, která určuje, zda ladicí program načítá nativní bitové kopie (NGen) z mezipaměti nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="e65e9-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e65e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e65e9-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="e65e9-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e65e9-105">Members</span></span>  
  
|<span data-ttu-id="e65e9-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="e65e9-106">Member name</span></span>|<span data-ttu-id="e65e9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e65e9-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="e65e9-108">V [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] aplikaci, používání imagí z mezipaměti nativní bitové kopie místní aplikace je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="e65e9-108">In a [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="e65e9-109">V desktopové aplikaci toto nastavení nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="e65e9-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e65e9-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e65e9-110">Remarks</span></span>  
 <span data-ttu-id="e65e9-111">`CorDebugNGENPolicy` Výčet je používán [icordebugprocess5::enablengenpolicy –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e65e9-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="e65e9-112">Zákaz použití obrázky z místní mezipaměti zajišťující konzistentní možnosti ladění tím, že zajišťuje, že ladicí program načte laditelné zkompilovaný pomocí kompilátoru JIT obrázky místo optimalizované nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="e65e9-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e65e9-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e65e9-113">Requirements</span></span>  
 <span data-ttu-id="e65e9-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e65e9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e65e9-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e65e9-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e65e9-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e65e9-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e65e9-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e65e9-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e65e9-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e65e9-118">See also</span></span>

- [<span data-ttu-id="e65e9-119">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="e65e9-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
