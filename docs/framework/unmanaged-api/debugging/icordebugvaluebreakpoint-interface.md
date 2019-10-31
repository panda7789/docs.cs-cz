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
ms.openlocfilehash: cee421ef7d7c856ba90dc21f4e9dc25ae6fe1a9b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140199"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="a4626-102">ICorDebugValueBreakpoint – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a4626-102">ICorDebugValueBreakpoint Interface</span></span>
<span data-ttu-id="a4626-103">Rozšiřuje rozhraní ICorDebugBreakpoint pro poskytnutí přístupu k určitým hodnotám.</span><span class="sxs-lookup"><span data-stu-id="a4626-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a4626-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a4626-104">Methods</span></span>  
  
|<span data-ttu-id="a4626-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a4626-105">Method</span></span>|<span data-ttu-id="a4626-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a4626-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a4626-107">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="a4626-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="a4626-108">Získá ukazatel rozhraní na objekt ICorDebugValue, který představuje hodnotu objektu, na kterém je nastavena zarážka.</span><span class="sxs-lookup"><span data-stu-id="a4626-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4626-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4626-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4626-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="a4626-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4626-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a4626-111">Requirements</span></span>  
 <span data-ttu-id="a4626-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4626-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4626-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a4626-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4626-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a4626-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4626-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4626-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4626-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4626-116">See also</span></span>

- [<span data-ttu-id="a4626-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a4626-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
