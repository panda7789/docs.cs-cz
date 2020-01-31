---
title: ICorDebugBreakpoint – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
ms.openlocfilehash: 53d8d219a13f2dade16a338efccf0837f8de0158
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784379"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="df47a-102">ICorDebugBreakpoint – rozhraní</span><span class="sxs-lookup"><span data-stu-id="df47a-102">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="df47a-103">Představuje zarážku ve funkci nebo bod sledování na hodnotě.</span><span class="sxs-lookup"><span data-stu-id="df47a-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="df47a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="df47a-104">Methods</span></span>  
  
|<span data-ttu-id="df47a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="df47a-105">Method</span></span>|<span data-ttu-id="df47a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="df47a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="df47a-107">Activate – metoda</span><span class="sxs-lookup"><span data-stu-id="df47a-107">Activate Method</span></span>](icordebugbreakpoint-activate-method.md)|<span data-ttu-id="df47a-108">Nastaví aktivní stav tohoto `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="df47a-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="df47a-109">IsActive – metoda</span><span class="sxs-lookup"><span data-stu-id="df47a-109">IsActive Method</span></span>](icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="df47a-110">Získá hodnotu, která označuje, zda je tato `ICorDebugBreakpoint` aktivní.</span><span class="sxs-lookup"><span data-stu-id="df47a-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df47a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="df47a-111">Remarks</span></span>  
 <span data-ttu-id="df47a-112">Zarážky přímo nepodporují podmíněné výrazy.</span><span class="sxs-lookup"><span data-stu-id="df47a-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="df47a-113">Pokud jsou takové funkce žádoucí, ladicí program je musí implementovat nad `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="df47a-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="df47a-114">Rozhraní ICorDebugFunctionBreakpoint rozšiřuje `ICorDebugBreakpoint` pro podporu zarážek v rámci funkcí.</span><span class="sxs-lookup"><span data-stu-id="df47a-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df47a-115">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="df47a-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df47a-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="df47a-116">Requirements</span></span>  
 <span data-ttu-id="df47a-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df47a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df47a-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="df47a-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df47a-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="df47a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df47a-120">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df47a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df47a-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="df47a-121">See also</span></span>

- [<span data-ttu-id="df47a-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="df47a-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
