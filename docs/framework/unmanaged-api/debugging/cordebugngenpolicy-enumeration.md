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
ms.openlocfilehash: 1ae40916807a86d1c9828080a6cb9e5c1d14c2ec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671223"
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="d23f4-102">CorDebugNGenPolicy – výčet</span><span class="sxs-lookup"><span data-stu-id="d23f4-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="d23f4-103">Poskytuje hodnotu, která určuje, zda ladicí program načítá nativní bitové kopie (NGen) z mezipaměti nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="d23f4-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d23f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d23f4-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="d23f4-105">Členové</span><span class="sxs-lookup"><span data-stu-id="d23f4-105">Members</span></span>  
  
|<span data-ttu-id="d23f4-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="d23f4-106">Member name</span></span>|<span data-ttu-id="d23f4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d23f4-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="d23f4-108">V [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] aplikaci, používání imagí z mezipaměti nativní bitové kopie místní aplikace je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="d23f4-108">In a [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="d23f4-109">V desktopové aplikaci toto nastavení nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="d23f4-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d23f4-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d23f4-110">Remarks</span></span>  
 <span data-ttu-id="d23f4-111">`CorDebugNGENPolicy` Výčet je používán [icordebugprocess5::enablengenpolicy –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="d23f4-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="d23f4-112">Zákaz použití obrázky z místní mezipaměti zajišťující konzistentní možnosti ladění tím, že zajišťuje, že ladicí program načte laditelné zkompilovaný pomocí kompilátoru JIT obrázky místo optimalizované nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="d23f4-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d23f4-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d23f4-113">Requirements</span></span>  
 <span data-ttu-id="d23f4-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d23f4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d23f4-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d23f4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d23f4-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d23f4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d23f4-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d23f4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d23f4-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d23f4-118">See also</span></span>
- [<span data-ttu-id="d23f4-119">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="d23f4-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
