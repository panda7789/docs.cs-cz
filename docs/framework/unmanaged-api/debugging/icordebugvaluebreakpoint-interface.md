---
title: ICorDebugValueBreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValueBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValueBreakpoint
helpviewer_keywords: ICorDebugValueBreakpoint interface [.NET Framework debugging]
ms.assetid: c02338fe-da6c-467f-9567-70ebb387e901
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 92de5aa960c9ded27aef09d2c795437e9c599835
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvaluebreakpoint-interface1"></a><span data-ttu-id="57da6-102">ICorDebugValueBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="57da6-102">ICorDebugValueBreakpoint Interface1</span></span>
<span data-ttu-id="57da6-103">Rozšiřuje rozhraní ICorDebugBreakpoint k poskytování přístupu k konkrétní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="57da6-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="57da6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="57da6-104">Methods</span></span>  
  
|<span data-ttu-id="57da6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="57da6-105">Method</span></span>|<span data-ttu-id="57da6-106">Popis</span><span class="sxs-lookup"><span data-stu-id="57da6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="57da6-107">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="57da6-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="57da6-108">Získá ukazatele rozhraní ICorDebugValue objektu, která představuje hodnotu objektu, na kterém je nastaven breakpoint.</span><span class="sxs-lookup"><span data-stu-id="57da6-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57da6-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="57da6-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57da6-110">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="57da6-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57da6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57da6-111">Requirements</span></span>  
 <span data-ttu-id="57da6-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57da6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57da6-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="57da6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57da6-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57da6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57da6-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57da6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57da6-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="57da6-116">See Also</span></span>  
 [<span data-ttu-id="57da6-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="57da6-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
