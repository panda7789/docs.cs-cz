---
title: Výčet CorDebugStateChange
ms.date: 03/30/2017
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f0f692b692628d50755ce813c66823f940dccb8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513782"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="a1070-102">Výčet CorDebugStateChange</span><span class="sxs-lookup"><span data-stu-id="a1070-102">CorDebugStateChange Enumeration</span></span>
<span data-ttu-id="a1070-103">Popisuje množství dat uložených v mezipaměti, který musí být odstraněn podle změn do procesu.</span><span class="sxs-lookup"><span data-stu-id="a1070-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1070-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1070-104">Syntax</span></span>  
  
```  
typedef enum CorDebugStateChange  
{  
    PROCESS_RUNNING = 0x0000001,   
    FLUSH_ALL       = 0x0000002,   
} CorDebugStateChange;  
```  
  
## <a name="members"></a><span data-ttu-id="a1070-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a1070-105">Members</span></span>  
  
|<span data-ttu-id="a1070-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a1070-106">Member</span></span>|<span data-ttu-id="a1070-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a1070-107">Description</span></span>|  
|------------|-----------------|  
|`PROCESS_RUNNING`|<span data-ttu-id="a1070-108">Proces byl dosažen nový stav paměti prostřednictvím dopředné spuštění.</span><span class="sxs-lookup"><span data-stu-id="a1070-108">The process reached a new memory state via forward execution.</span></span>|  
|`SET_CONTEXT_FLAG_UNWIND_FRAME`|<span data-ttu-id="a1070-109">Paměť procesu může být libovolně jiný než dříve.</span><span class="sxs-lookup"><span data-stu-id="a1070-109">The process' memory may be arbitrarily different than it was previously.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1070-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1070-110">Remarks</span></span>  
 <span data-ttu-id="a1070-111">Člen `CorDebugStateChange` výčtu je zadaný jako argument při volání ladicího programu [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) – metoda</span><span class="sxs-lookup"><span data-stu-id="a1070-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) method</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1070-112">Tento výčet je určena pro použití v .NET Native ladění pouze scénáře.</span><span class="sxs-lookup"><span data-stu-id="a1070-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1070-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1070-113">Requirements</span></span>  
 <span data-ttu-id="a1070-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1070-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1070-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1070-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1070-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1070-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1070-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1070-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1070-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1070-118">See also</span></span>
- [<span data-ttu-id="a1070-119">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="a1070-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="a1070-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="a1070-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
