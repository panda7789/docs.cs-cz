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
ms.openlocfilehash: f77268e069d322d0f491f78b154cf63b691e3e38
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966813"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="f8f67-102">ICorDebugValueBreakpoint – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8f67-102">ICorDebugValueBreakpoint Interface</span></span>
<span data-ttu-id="f8f67-103">Rozšiřuje rozhraní ICorDebugBreakpoint pro poskytnutí přístupu k určitým hodnotám.</span><span class="sxs-lookup"><span data-stu-id="f8f67-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8f67-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f8f67-104">Methods</span></span>  
  
|<span data-ttu-id="f8f67-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f8f67-105">Method</span></span>|<span data-ttu-id="f8f67-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f8f67-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8f67-107">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="f8f67-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="f8f67-108">Získá ukazatel rozhraní na objekt ICorDebugValue, který představuje hodnotu objektu, na kterém je nastavena zarážka.</span><span class="sxs-lookup"><span data-stu-id="f8f67-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8f67-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f8f67-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8f67-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="f8f67-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8f67-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8f67-111">Requirements</span></span>  
 <span data-ttu-id="f8f67-112">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8f67-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8f67-113">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f8f67-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8f67-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8f67-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8f67-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8f67-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8f67-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8f67-116">See also</span></span>

- [<span data-ttu-id="f8f67-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f8f67-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
