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
ms.openlocfilehash: 841108457293e3377ee87f9c7d7c6898340e51b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404343"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="fa9b4-102">Výčet CorDebugStateChange</span><span class="sxs-lookup"><span data-stu-id="fa9b4-102">CorDebugStateChange Enumeration</span></span>
<span data-ttu-id="fa9b4-103">Popisuje množství uložené v mezipaměti dat, která musí být odstraněn podle změn do procesu.</span><span class="sxs-lookup"><span data-stu-id="fa9b4-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa9b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa9b4-104">Syntax</span></span>  
  
```  
typedef enum CorDebugStateChange  
{  
    PROCESS_RUNNING = 0x0000001,   
    FLUSH_ALL       = 0x0000002,   
} CorDebugStateChange;  
```  
  
## <a name="members"></a><span data-ttu-id="fa9b4-105">Členové</span><span class="sxs-lookup"><span data-stu-id="fa9b4-105">Members</span></span>  
  
|<span data-ttu-id="fa9b4-106">Člen</span><span class="sxs-lookup"><span data-stu-id="fa9b4-106">Member</span></span>|<span data-ttu-id="fa9b4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="fa9b4-107">Description</span></span>|  
|------------|-----------------|  
|`PROCESS_RUNNING`|<span data-ttu-id="fa9b4-108">Proces dosaženo nový stav paměti prostřednictvím dopředného provádění.</span><span class="sxs-lookup"><span data-stu-id="fa9b4-108">The process reached a new memory state via forward execution.</span></span>|  
|`SET_CONTEXT_FLAG_UNWIND_FRAME`|<span data-ttu-id="fa9b4-109">Paměť se proces může být nahodile jiný než dříve.</span><span class="sxs-lookup"><span data-stu-id="fa9b4-109">The process' memory may be arbitrarily different than it was previously.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa9b4-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fa9b4-110">Remarks</span></span>  
 <span data-ttu-id="fa9b4-111">Člen `CorDebugStateChange` výčtu je zadaný jako argument při volání ladicí program [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) – metoda</span><span class="sxs-lookup"><span data-stu-id="fa9b4-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) method</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa9b4-112">Tento výčet je určena pro použití v rozhraní .NET nativní ladění pouze scénáře.</span><span class="sxs-lookup"><span data-stu-id="fa9b4-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa9b4-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fa9b4-113">Requirements</span></span>  
 <span data-ttu-id="fa9b4-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa9b4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa9b4-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa9b4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa9b4-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa9b4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa9b4-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa9b4-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa9b4-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="fa9b4-118">See Also</span></span>  
 [<span data-ttu-id="fa9b4-119">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="fa9b4-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="fa9b4-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="fa9b4-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
