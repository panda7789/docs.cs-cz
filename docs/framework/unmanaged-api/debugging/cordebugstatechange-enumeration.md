---
title: "Výčet CorDebugStateChange"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugStateChange
api_location: mscordbi.dll
api_type: COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: caf49621342be0ff85ac3cb56b95bb87f524c3be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="64996-102">Výčet CorDebugStateChange</span><span class="sxs-lookup"><span data-stu-id="64996-102">CorDebugStateChange Enumeration</span></span>
<span data-ttu-id="64996-103">Popisuje množství uložené v mezipaměti dat, která musí být odstraněn podle změn do procesu.</span><span class="sxs-lookup"><span data-stu-id="64996-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64996-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64996-104">Syntax</span></span>  
  
```  
typedef enum CorDebugStateChange  
{  
    PROCESS_RUNNING = 0x0000001,   
    FLUSH_ALL       = 0x0000002,   
} CorDebugStateChange;  
```  
  
## <a name="members"></a><span data-ttu-id="64996-105">Členové</span><span class="sxs-lookup"><span data-stu-id="64996-105">Members</span></span>  
  
|<span data-ttu-id="64996-106">Člen</span><span class="sxs-lookup"><span data-stu-id="64996-106">Member</span></span>|<span data-ttu-id="64996-107">Popis</span><span class="sxs-lookup"><span data-stu-id="64996-107">Description</span></span>|  
|------------|-----------------|  
|`PROCESS_RUNNING`|<span data-ttu-id="64996-108">Proces dosaženo nový stav paměti prostřednictvím dopředného provádění.</span><span class="sxs-lookup"><span data-stu-id="64996-108">The process reached a new memory state via forward execution.</span></span>|  
|`SET_CONTEXT_FLAG_UNWIND_FRAME`|<span data-ttu-id="64996-109">Paměť se proces může být nahodile jiný než dříve.</span><span class="sxs-lookup"><span data-stu-id="64996-109">The process' memory may be arbitrarily different than it was previously.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64996-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="64996-110">Remarks</span></span>  
 <span data-ttu-id="64996-111">Člen `CorDebugStateChange` výčtu je zadaný jako argument při volání ladicí program [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) – metoda</span><span class="sxs-lookup"><span data-stu-id="64996-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) method</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64996-112">Tento výčet je určena pro použití v rozhraní .NET nativní ladění pouze scénáře.</span><span class="sxs-lookup"><span data-stu-id="64996-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64996-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="64996-113">Requirements</span></span>  
 <span data-ttu-id="64996-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64996-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64996-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64996-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64996-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64996-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64996-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64996-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64996-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="64996-118">See Also</span></span>  
 [<span data-ttu-id="64996-119">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="64996-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="64996-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="64996-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
