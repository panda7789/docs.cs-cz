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
ms.openlocfilehash: 2f8337f96239948189ffd58923d87fd05c79b0c3
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204866"
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="1d895-102">CorDebugNGenPolicy – výčet</span><span class="sxs-lookup"><span data-stu-id="1d895-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="1d895-103">Poskytuje hodnotu, která určuje, zda ladicí program načte nativní bitové kopie (NGen) z mezipaměti nativních imagí.</span><span class="sxs-lookup"><span data-stu-id="1d895-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d895-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d895-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="1d895-105">Members</span><span class="sxs-lookup"><span data-stu-id="1d895-105">Members</span></span>  
  
|<span data-ttu-id="1d895-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="1d895-106">Member name</span></span>|<span data-ttu-id="1d895-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1d895-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="1d895-108">V aplikaci pro Windows 8. x Store je použití imagí z místní mezipaměti nativních imagí zakázané.</span><span class="sxs-lookup"><span data-stu-id="1d895-108">In a Windows 8.x Store app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="1d895-109">V desktopové aplikaci nemá toto nastavení žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="1d895-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d895-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1d895-110">Remarks</span></span>  
 <span data-ttu-id="1d895-111">`CorDebugNGENPolicy` výčet používá metoda [ICorDebugProcess5:: EnableNGENPolicy –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1d895-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="1d895-112">Zakázání použití imagí z místní mezipaměti nativních imagí poskytuje konzistentní možnosti ladění tím, že zajistí, že ladicí program načte místo optimalizovaných nativních imagí laditelné obrázky kompilované JIT.</span><span class="sxs-lookup"><span data-stu-id="1d895-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d895-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1d895-113">Requirements</span></span>  
 <span data-ttu-id="1d895-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d895-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d895-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1d895-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d895-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1d895-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d895-117">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d895-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d895-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d895-118">See also</span></span>

- [<span data-ttu-id="1d895-119">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="1d895-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
