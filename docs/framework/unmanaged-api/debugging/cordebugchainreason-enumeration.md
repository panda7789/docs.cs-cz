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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e46118e97a4b888a16f12cf6705d2b7e67bbf7ec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740357"
---
# <a name="cordebugchainreason-enumeration"></a><span data-ttu-id="0ecb2-102">CorDebugChainReason – výčet</span><span class="sxs-lookup"><span data-stu-id="0ecb2-102">CorDebugChainReason Enumeration</span></span>
<span data-ttu-id="0ecb2-103">Označuje důvod nebo důvodů, proč inicializační řetězec volání.</span><span class="sxs-lookup"><span data-stu-id="0ecb2-103">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ecb2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ecb2-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="0ecb2-105">Členové</span><span class="sxs-lookup"><span data-stu-id="0ecb2-105">Members</span></span>  
  
|<span data-ttu-id="0ecb2-106">Člen</span><span class="sxs-lookup"><span data-stu-id="0ecb2-106">Member</span></span>|<span data-ttu-id="0ecb2-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0ecb2-107">Description</span></span>|  
|------------|-----------------|  
|`CHAIN_NONE`|<span data-ttu-id="0ecb2-108">Bylo zahájeno žádný řetězec volání.</span><span class="sxs-lookup"><span data-stu-id="0ecb2-108">No call chain has been initiated.</span></span>|  
|`CHAIN_CLASS_INIT`|<span data-ttu-id="0ecb2-109">Řetězec byl inicializován nástrojem konstruktor.</span><span class="sxs-lookup"><span data-stu-id="0ecb2-109">The chain was initiated by a constructor.</span></span>|  
|`CHAIN_EXCEPTION_FILTER`|<span data-ttu-id="0ecb2-110">Řetězec byl inicializován nástrojem filtr výjimek.</span><span class="sxs-lookup"><span data-stu-id="0ecb2-110">The chain was initiated by an exception filter.</span></span>|  
|`CHAIN_SECURITY`|<span data-ttu-id="0ecb2-111">Řetězec byl inicializován nástrojem kód, který vynucuje zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0ecb2-111">The chain was initiated by code that enforces security.</span></span>|  
|`CHAIN_CONTEXT_POLICY`|<span data-ttu-id="0ecb2-112">Řetězec byl inicializován nástrojem zásadu kontextu.</span><span class="sxs-lookup"><span data-stu-id="0ecb2-112">The chain was initiated by a context policy.</span></span>|  
|`CHAIN_INTERCEPTION`|<span data-ttu-id="0ecb2-113">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="0ecb2-113">Not used.</span></span>|  
|`CHAIN_PROCESS_START`|<span data-ttu-id="0ecb2-114">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="0ecb2-114">Not used.</span></span>|  
|`CHAIN_THREAD_START`|<span data-ttu-id="0ecb2-115">Řetězec byl inicializován nástrojem začátku spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="0ecb2-115">The chain was initiated by the start of a thread execution.</span></span>|  
|`CHAIN_ENTER_MANAGED`|<span data-ttu-id="0ecb2-116">Řetězec byl inicializován nástrojem položku do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="0ecb2-116">The chain was initiated by entry into managed code.</span></span>|  
|`CHAIN_ENTER_UNMANAGED`|<span data-ttu-id="0ecb2-117">Řetězec byl inicializován nástrojem vstupem nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="0ecb2-117">The chain was initiated by entry into unmanaged code.</span></span>|  
|`CHAIN_DEBUGGER_EVAL`|<span data-ttu-id="0ecb2-118">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="0ecb2-118">Not used.</span></span>|  
|`CHAIN_CONTEXT_SWITCH`|<span data-ttu-id="0ecb2-119">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="0ecb2-119">Not used.</span></span>|  
|`CHAIN_FUNC_EVAL`|<span data-ttu-id="0ecb2-120">Řetězec byl inicializován nástrojem vyhodnocení funkce.</span><span class="sxs-lookup"><span data-stu-id="0ecb2-120">The chain was initiated by a function evaluation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ecb2-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ecb2-121">Remarks</span></span>  
 <span data-ttu-id="0ecb2-122">Použití [icordebugchain::getreason –](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) metoda zjistit důvody pro zahájení řetěz volání.</span><span class="sxs-lookup"><span data-stu-id="0ecb2-122">Use the [ICorDebugChain::GetReason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) method to ascertain the reasons for the initiation of a call chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ecb2-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ecb2-123">Requirements</span></span>  
 <span data-ttu-id="0ecb2-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ecb2-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ecb2-125">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ecb2-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ecb2-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ecb2-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ecb2-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ecb2-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ecb2-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ecb2-128">See also</span></span>

- [<span data-ttu-id="0ecb2-129">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="0ecb2-129">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
