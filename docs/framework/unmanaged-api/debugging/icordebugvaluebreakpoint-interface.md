---
title: ICorDebugValueBreakpoint – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugValueBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint
helpviewer_keywords:
- ICorDebugValueBreakpoint interface [.NET Framework debugging]
ms.assetid: c02338fe-da6c-467f-9567-70ebb387e901
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 778359a7d26b6e2f19984a1f7ff06a527f2449f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167743"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="e1694-102">ICorDebugValueBreakpoint – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e1694-102">ICorDebugValueBreakpoint Interface</span></span>
<span data-ttu-id="e1694-103">Rozšiřuje icordebugbreakpoint – rozhraní pro poskytnutí přístupu k určitým hodnotám.</span><span class="sxs-lookup"><span data-stu-id="e1694-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e1694-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e1694-104">Methods</span></span>  
  
|<span data-ttu-id="e1694-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e1694-105">Method</span></span>|<span data-ttu-id="e1694-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e1694-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e1694-107">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="e1694-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="e1694-108">Získá ukazatel rozhraní na ICorDebugValue objekt, který představuje hodnotu objektu, na kterém je nastavena zarážka.</span><span class="sxs-lookup"><span data-stu-id="e1694-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1694-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e1694-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1694-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="e1694-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1694-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e1694-111">Requirements</span></span>  
 <span data-ttu-id="e1694-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1694-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1694-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1694-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1694-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1694-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e1694-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e1694-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e1694-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1694-116">See also</span></span>

- [<span data-ttu-id="e1694-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e1694-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
