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
ms.openlocfilehash: e4c291c12de9cb95416e12e1a5fca273c542df36
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966357"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="90ea8-102">ICorDebugValueBreakpoint – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90ea8-102">ICorDebugValueBreakpoint Interface</span></span>
<span data-ttu-id="90ea8-103">Rozšiřuje icordebugbreakpoint – rozhraní pro poskytnutí přístupu k určitým hodnotám.</span><span class="sxs-lookup"><span data-stu-id="90ea8-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="90ea8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="90ea8-104">Methods</span></span>  
  
|<span data-ttu-id="90ea8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="90ea8-105">Method</span></span>|<span data-ttu-id="90ea8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="90ea8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="90ea8-107">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="90ea8-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="90ea8-108">Získá ukazatel rozhraní na ICorDebugValue objekt, který představuje hodnotu objektu, na kterém je nastavena zarážka.</span><span class="sxs-lookup"><span data-stu-id="90ea8-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90ea8-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90ea8-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90ea8-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="90ea8-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90ea8-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90ea8-111">Requirements</span></span>  
 <span data-ttu-id="90ea8-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90ea8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90ea8-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90ea8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90ea8-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90ea8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90ea8-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90ea8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90ea8-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90ea8-116">See also</span></span>
- [<span data-ttu-id="90ea8-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="90ea8-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
