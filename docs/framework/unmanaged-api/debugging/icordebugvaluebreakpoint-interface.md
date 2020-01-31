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
ms.openlocfilehash: e1bb5a6fd0550f7c25d46fa31ca11a10cec54986
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791079"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="a0c3f-102">ICorDebugValueBreakpoint – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0c3f-102">ICorDebugValueBreakpoint Interface</span></span>
<span data-ttu-id="a0c3f-103">Rozšiřuje rozhraní ICorDebugBreakpoint pro poskytnutí přístupu k určitým hodnotám.</span><span class="sxs-lookup"><span data-stu-id="a0c3f-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a0c3f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a0c3f-104">Methods</span></span>  
  
|<span data-ttu-id="a0c3f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a0c3f-105">Method</span></span>|<span data-ttu-id="a0c3f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a0c3f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a0c3f-107">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="a0c3f-107">GetValue Method</span></span>](icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="a0c3f-108">Získá ukazatel rozhraní na objekt ICorDebugValue, který představuje hodnotu objektu, na kterém je nastavena zarážka.</span><span class="sxs-lookup"><span data-stu-id="a0c3f-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0c3f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0c3f-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a0c3f-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="a0c3f-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0c3f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a0c3f-111">Requirements</span></span>  
 <span data-ttu-id="a0c3f-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0c3f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0c3f-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a0c3f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0c3f-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a0c3f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0c3f-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0c3f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0c3f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0c3f-116">See also</span></span>

- [<span data-ttu-id="a0c3f-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a0c3f-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
