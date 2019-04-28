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
ms.openlocfilehash: cac790ebbf25ee3095db293ba90612be37fff9b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609227"
---
# <a name="cordebugchainreason-enumeration"></a><span data-ttu-id="849ee-102">CorDebugChainReason – výčet</span><span class="sxs-lookup"><span data-stu-id="849ee-102">CorDebugChainReason Enumeration</span></span>
<span data-ttu-id="849ee-103">Označuje důvod nebo důvodů, proč inicializační řetězec volání.</span><span class="sxs-lookup"><span data-stu-id="849ee-103">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="849ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="849ee-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="849ee-105">Členové</span><span class="sxs-lookup"><span data-stu-id="849ee-105">Members</span></span>  
  
|<span data-ttu-id="849ee-106">Člen</span><span class="sxs-lookup"><span data-stu-id="849ee-106">Member</span></span>|<span data-ttu-id="849ee-107">Popis</span><span class="sxs-lookup"><span data-stu-id="849ee-107">Description</span></span>|  
|------------|-----------------|  
|`CHAIN_NONE`|<span data-ttu-id="849ee-108">Bylo zahájeno žádný řetězec volání.</span><span class="sxs-lookup"><span data-stu-id="849ee-108">No call chain has been initiated.</span></span>|  
|`CHAIN_CLASS_INIT`|<span data-ttu-id="849ee-109">Řetězec byl inicializován nástrojem konstruktor.</span><span class="sxs-lookup"><span data-stu-id="849ee-109">The chain was initiated by a constructor.</span></span>|  
|`CHAIN_EXCEPTION_FILTER`|<span data-ttu-id="849ee-110">Řetězec byl inicializován nástrojem filtr výjimek.</span><span class="sxs-lookup"><span data-stu-id="849ee-110">The chain was initiated by an exception filter.</span></span>|  
|`CHAIN_SECURITY`|<span data-ttu-id="849ee-111">Řetězec byl inicializován nástrojem kód, který vynucuje zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="849ee-111">The chain was initiated by code that enforces security.</span></span>|  
|`CHAIN_CONTEXT_POLICY`|<span data-ttu-id="849ee-112">Řetězec byl inicializován nástrojem zásadu kontextu.</span><span class="sxs-lookup"><span data-stu-id="849ee-112">The chain was initiated by a context policy.</span></span>|  
|`CHAIN_INTERCEPTION`|<span data-ttu-id="849ee-113">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="849ee-113">Not used.</span></span>|  
|`CHAIN_PROCESS_START`|<span data-ttu-id="849ee-114">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="849ee-114">Not used.</span></span>|  
|`CHAIN_THREAD_START`|<span data-ttu-id="849ee-115">Řetězec byl inicializován nástrojem začátku spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="849ee-115">The chain was initiated by the start of a thread execution.</span></span>|  
|`CHAIN_ENTER_MANAGED`|<span data-ttu-id="849ee-116">Řetězec byl inicializován nástrojem položku do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="849ee-116">The chain was initiated by entry into managed code.</span></span>|  
|`CHAIN_ENTER_UNMANAGED`|<span data-ttu-id="849ee-117">Řetězec byl inicializován nástrojem vstupem nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="849ee-117">The chain was initiated by entry into unmanaged code.</span></span>|  
|`CHAIN_DEBUGGER_EVAL`|<span data-ttu-id="849ee-118">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="849ee-118">Not used.</span></span>|  
|`CHAIN_CONTEXT_SWITCH`|<span data-ttu-id="849ee-119">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="849ee-119">Not used.</span></span>|  
|`CHAIN_FUNC_EVAL`|<span data-ttu-id="849ee-120">Řetězec byl inicializován nástrojem vyhodnocení funkce.</span><span class="sxs-lookup"><span data-stu-id="849ee-120">The chain was initiated by a function evaluation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="849ee-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="849ee-121">Remarks</span></span>  
 <span data-ttu-id="849ee-122">Použití [icordebugchain::getreason –](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) metoda zjistit důvody pro zahájení řetěz volání.</span><span class="sxs-lookup"><span data-stu-id="849ee-122">Use the [ICorDebugChain::GetReason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) method to ascertain the reasons for the initiation of a call chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="849ee-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="849ee-123">Requirements</span></span>  
 <span data-ttu-id="849ee-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="849ee-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="849ee-125">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="849ee-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="849ee-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="849ee-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="849ee-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="849ee-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="849ee-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="849ee-128">See also</span></span>

- [<span data-ttu-id="849ee-129">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="849ee-129">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
