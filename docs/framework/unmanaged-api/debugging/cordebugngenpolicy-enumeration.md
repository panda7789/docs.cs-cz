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
ms.openlocfilehash: 036d3f12b38c19259fefaba674d0f9025a58d688
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795752"
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="af8df-102">CorDebugNGenPolicy – výčet</span><span class="sxs-lookup"><span data-stu-id="af8df-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="af8df-103">Poskytuje hodnotu, která určuje, zda ladicí program načte nativní bitové kopie (NGen) z mezipaměti nativních imagí.</span><span class="sxs-lookup"><span data-stu-id="af8df-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af8df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af8df-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="af8df-105">Členové</span><span class="sxs-lookup"><span data-stu-id="af8df-105">Members</span></span>  
  
|<span data-ttu-id="af8df-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="af8df-106">Member name</span></span>|<span data-ttu-id="af8df-107">Popis</span><span class="sxs-lookup"><span data-stu-id="af8df-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="af8df-108">V aplikaci pro Windows 8. x Store je použití imagí z místní mezipaměti nativních imagí zakázané.</span><span class="sxs-lookup"><span data-stu-id="af8df-108">In a Windows 8.x Store app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="af8df-109">V desktopové aplikaci nemá toto nastavení žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="af8df-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af8df-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="af8df-110">Remarks</span></span>  
 <span data-ttu-id="af8df-111">`CorDebugNGENPolicy` Výčet je používán metodou [ICorDebugProcess5:: EnableNGENPolicy –](icordebugprocess5-enablengenpolicy-method.md) .</span><span class="sxs-lookup"><span data-stu-id="af8df-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="af8df-112">Zakázání použití imagí z místní mezipaměti nativních imagí poskytuje konzistentní možnosti ladění tím, že zajistí, že ladicí program načte místo optimalizovaných nativních imagí laditelné obrázky kompilované JIT.</span><span class="sxs-lookup"><span data-stu-id="af8df-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af8df-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="af8df-113">Requirements</span></span>  
 <span data-ttu-id="af8df-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af8df-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af8df-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="af8df-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af8df-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="af8df-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af8df-117">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af8df-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af8df-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="af8df-118">See also</span></span>

- [<span data-ttu-id="af8df-119">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="af8df-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
