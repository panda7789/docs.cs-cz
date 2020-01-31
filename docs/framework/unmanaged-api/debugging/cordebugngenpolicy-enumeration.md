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
ms.openlocfilehash: de0e07429187f1ec484942d522cdf57f819d553a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789300"
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="58623-102">CorDebugNGenPolicy – výčet</span><span class="sxs-lookup"><span data-stu-id="58623-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="58623-103">Poskytuje hodnotu, která určuje, zda ladicí program načte nativní bitové kopie (NGen) z mezipaměti nativních imagí.</span><span class="sxs-lookup"><span data-stu-id="58623-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58623-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58623-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="58623-105">Členové</span><span class="sxs-lookup"><span data-stu-id="58623-105">Members</span></span>  
  
|<span data-ttu-id="58623-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="58623-106">Member name</span></span>|<span data-ttu-id="58623-107">Popis</span><span class="sxs-lookup"><span data-stu-id="58623-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="58623-108">V aplikaci pro Windows 8. x Store je použití imagí z místní mezipaměti nativních imagí zakázané.</span><span class="sxs-lookup"><span data-stu-id="58623-108">In a Windows 8.x Store app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="58623-109">V desktopové aplikaci nemá toto nastavení žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="58623-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58623-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="58623-110">Remarks</span></span>  
 <span data-ttu-id="58623-111">`CorDebugNGENPolicy` výčet používá metoda [ICorDebugProcess5:: EnableNGENPolicy –](icordebugprocess5-enablengenpolicy-method.md) .</span><span class="sxs-lookup"><span data-stu-id="58623-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="58623-112">Zakázání použití imagí z místní mezipaměti nativních imagí poskytuje konzistentní možnosti ladění tím, že zajistí, že ladicí program načte místo optimalizovaných nativních imagí laditelné obrázky kompilované JIT.</span><span class="sxs-lookup"><span data-stu-id="58623-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58623-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="58623-113">Requirements</span></span>  
 <span data-ttu-id="58623-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58623-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58623-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="58623-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58623-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="58623-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58623-117">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58623-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58623-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58623-118">See also</span></span>

- [<span data-ttu-id="58623-119">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="58623-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
