---
title: "CorDebugChainReason – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugChainReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugChainReason
helpviewer_keywords: CorDebugChainReason enumeration [.NET Framework debugging]
ms.assetid: c915da51-50b2-41df-841a-2b971f4d0975
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0d501db111256861a3d0a602712e4c32f40b7b6e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugchainreason-enumeration"></a><span data-ttu-id="99414-102">CorDebugChainReason – výčet</span><span class="sxs-lookup"><span data-stu-id="99414-102">CorDebugChainReason Enumeration</span></span>
<span data-ttu-id="99414-103">Označuje důvod nebo důvody pro zahájení řetěz volání.</span><span class="sxs-lookup"><span data-stu-id="99414-103">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99414-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99414-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="99414-105">Členové</span><span class="sxs-lookup"><span data-stu-id="99414-105">Members</span></span>  
  
|<span data-ttu-id="99414-106">Člen</span><span class="sxs-lookup"><span data-stu-id="99414-106">Member</span></span>|<span data-ttu-id="99414-107">Popis</span><span class="sxs-lookup"><span data-stu-id="99414-107">Description</span></span>|  
|------------|-----------------|  
|`CHAIN_NONE`|<span data-ttu-id="99414-108">Byla inicializována žádné řetěz volání.</span><span class="sxs-lookup"><span data-stu-id="99414-108">No call chain has been initiated.</span></span>|  
|`CHAIN_CLASS_INIT`|<span data-ttu-id="99414-109">Řetězu byl inicializován nástrojem konstruktor.</span><span class="sxs-lookup"><span data-stu-id="99414-109">The chain was initiated by a constructor.</span></span>|  
|`CHAIN_EXCEPTION_FILTER`|<span data-ttu-id="99414-110">Řetězu byl inicializován nástrojem filtru výjimek.</span><span class="sxs-lookup"><span data-stu-id="99414-110">The chain was initiated by an exception filter.</span></span>|  
|`CHAIN_SECURITY`|<span data-ttu-id="99414-111">Řetězu byl inicializován nástrojem kód, který vynucuje zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="99414-111">The chain was initiated by code that enforces security.</span></span>|  
|`CHAIN_CONTEXT_POLICY`|<span data-ttu-id="99414-112">Řetězu byl inicializován nástrojem zásadu kontextu.</span><span class="sxs-lookup"><span data-stu-id="99414-112">The chain was initiated by a context policy.</span></span>|  
|`CHAIN_INTERCEPTION`|<span data-ttu-id="99414-113">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="99414-113">Not used.</span></span>|  
|`CHAIN_PROCESS_START`|<span data-ttu-id="99414-114">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="99414-114">Not used.</span></span>|  
|`CHAIN_THREAD_START`|<span data-ttu-id="99414-115">Řetězu byl inicializován nástrojem spuštění provádění vlákna.</span><span class="sxs-lookup"><span data-stu-id="99414-115">The chain was initiated by the start of a thread execution.</span></span>|  
|`CHAIN_ENTER_MANAGED`|<span data-ttu-id="99414-116">Řetězu byl inicializován nástrojem položku do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="99414-116">The chain was initiated by entry into managed code.</span></span>|  
|`CHAIN_ENTER_UNMANAGED`|<span data-ttu-id="99414-117">Řetězu byl inicializován nástrojem položka nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="99414-117">The chain was initiated by entry into unmanaged code.</span></span>|  
|`CHAIN_DEBUGGER_EVAL`|<span data-ttu-id="99414-118">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="99414-118">Not used.</span></span>|  
|`CHAIN_CONTEXT_SWITCH`|<span data-ttu-id="99414-119">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="99414-119">Not used.</span></span>|  
|`CHAIN_FUNC_EVAL`|<span data-ttu-id="99414-120">Řetězu byl inicializován nástrojem vyhodnocení funkce.</span><span class="sxs-lookup"><span data-stu-id="99414-120">The chain was initiated by a function evaluation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99414-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="99414-121">Remarks</span></span>  
 <span data-ttu-id="99414-122">Použití [icordebugchain::getreason –](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) metoda zjistit důvody pro zahájení řetěz volání.</span><span class="sxs-lookup"><span data-stu-id="99414-122">Use the [ICorDebugChain::GetReason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) method to ascertain the reasons for the initiation of a call chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99414-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="99414-123">Requirements</span></span>  
 <span data-ttu-id="99414-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99414-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99414-125">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99414-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99414-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99414-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99414-127">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99414-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99414-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="99414-128">See Also</span></span>  
 [<span data-ttu-id="99414-129">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="99414-129">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
