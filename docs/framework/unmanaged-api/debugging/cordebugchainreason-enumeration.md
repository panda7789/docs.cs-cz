---
title: CorDebugChainReason – výčet
ms.date: 03/30/2017
api_name:
- CorDebugChainReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugChainReason
helpviewer_keywords:
- CorDebugChainReason enumeration [.NET Framework debugging]
ms.assetid: c915da51-50b2-41df-841a-2b971f4d0975
topic_type:
- apiref
ms.openlocfilehash: 2f53e3e938f62e714bf421ee7ba0cbf0a47b9f8e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132281"
---
# <a name="cordebugchainreason-enumeration"></a><span data-ttu-id="3fd94-102">CorDebugChainReason – výčet</span><span class="sxs-lookup"><span data-stu-id="3fd94-102">CorDebugChainReason Enumeration</span></span>
<span data-ttu-id="3fd94-103">Určuje důvod nebo důvody pro zahájení řetězu volání.</span><span class="sxs-lookup"><span data-stu-id="3fd94-103">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fd94-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fd94-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugChainReason {  
    CHAIN_NONE              = 0x000,  
    CHAIN_CLASS_INIT        = 0x001,  
    CHAIN_EXCEPTION_FILTER  = 0x002,  
    CHAIN_SECURITY          = 0x004,  
    CHAIN_CONTEXT_POLICY    = 0x008,  
    CHAIN_INTERCEPTION      = 0x010,  
    CHAIN_PROCESS_START     = 0x020,  
    CHAIN_THREAD_START      = 0x040,  
    CHAIN_ENTER_MANAGED     = 0x080,  
    CHAIN_ENTER_UNMANAGED   = 0x100,  
    CHAIN_DEBUGGER_EVAL     = 0x200,  
    CHAIN_CONTEXT_SWITCH    = 0x400,  
    CHAIN_FUNC_EVAL         = 0x800  
} CorDebugChainReason;  
```  
  
## <a name="members"></a><span data-ttu-id="3fd94-105">Členové</span><span class="sxs-lookup"><span data-stu-id="3fd94-105">Members</span></span>  
  
|<span data-ttu-id="3fd94-106">Člen</span><span class="sxs-lookup"><span data-stu-id="3fd94-106">Member</span></span>|<span data-ttu-id="3fd94-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3fd94-107">Description</span></span>|  
|------------|-----------------|  
|`CHAIN_NONE`|<span data-ttu-id="3fd94-108">Neinicioval se žádný řetěz volání.</span><span class="sxs-lookup"><span data-stu-id="3fd94-108">No call chain has been initiated.</span></span>|  
|`CHAIN_CLASS_INIT`|<span data-ttu-id="3fd94-109">Řetěz byl iniciován konstruktorem.</span><span class="sxs-lookup"><span data-stu-id="3fd94-109">The chain was initiated by a constructor.</span></span>|  
|`CHAIN_EXCEPTION_FILTER`|<span data-ttu-id="3fd94-110">Řetěz byl iniciován filtrem výjimky.</span><span class="sxs-lookup"><span data-stu-id="3fd94-110">The chain was initiated by an exception filter.</span></span>|  
|`CHAIN_SECURITY`|<span data-ttu-id="3fd94-111">Řetězec byl iniciován kódem, který vynutil zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3fd94-111">The chain was initiated by code that enforces security.</span></span>|  
|`CHAIN_CONTEXT_POLICY`|<span data-ttu-id="3fd94-112">Řetěz byl iniciován zásadami kontextu.</span><span class="sxs-lookup"><span data-stu-id="3fd94-112">The chain was initiated by a context policy.</span></span>|  
|`CHAIN_INTERCEPTION`|<span data-ttu-id="3fd94-113">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="3fd94-113">Not used.</span></span>|  
|`CHAIN_PROCESS_START`|<span data-ttu-id="3fd94-114">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="3fd94-114">Not used.</span></span>|  
|`CHAIN_THREAD_START`|<span data-ttu-id="3fd94-115">Řetěz byl iniciován zahájením provádění vlákna.</span><span class="sxs-lookup"><span data-stu-id="3fd94-115">The chain was initiated by the start of a thread execution.</span></span>|  
|`CHAIN_ENTER_MANAGED`|<span data-ttu-id="3fd94-116">Řetězec byl iniciován zadáním do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="3fd94-116">The chain was initiated by entry into managed code.</span></span>|  
|`CHAIN_ENTER_UNMANAGED`|<span data-ttu-id="3fd94-117">Řetězec byl iniciován vložením do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="3fd94-117">The chain was initiated by entry into unmanaged code.</span></span>|  
|`CHAIN_DEBUGGER_EVAL`|<span data-ttu-id="3fd94-118">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="3fd94-118">Not used.</span></span>|  
|`CHAIN_CONTEXT_SWITCH`|<span data-ttu-id="3fd94-119">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="3fd94-119">Not used.</span></span>|  
|`CHAIN_FUNC_EVAL`|<span data-ttu-id="3fd94-120">Řetěz byl iniciován vyhodnocením funkce.</span><span class="sxs-lookup"><span data-stu-id="3fd94-120">The chain was initiated by a function evaluation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fd94-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3fd94-121">Remarks</span></span>  
 <span data-ttu-id="3fd94-122">Použijte metodu [ICorDebugChain:: getdůvod](icordebugchain-getreason-method.md) k zjištění důvodů pro zahájení řetězu volání.</span><span class="sxs-lookup"><span data-stu-id="3fd94-122">Use the [ICorDebugChain::GetReason](icordebugchain-getreason-method.md) method to ascertain the reasons for the initiation of a call chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fd94-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3fd94-123">Requirements</span></span>  
 <span data-ttu-id="3fd94-124">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fd94-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fd94-125">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3fd94-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3fd94-126">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3fd94-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fd94-127">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fd94-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fd94-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3fd94-128">See also</span></span>

- [<span data-ttu-id="3fd94-129">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="3fd94-129">Debugging Enumerations</span></span>](debugging-enumerations.md)
