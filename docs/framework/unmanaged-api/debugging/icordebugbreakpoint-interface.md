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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 608c2cea79c20a43d65fcbf37ba13242fa465100
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969314"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="ea2d1-102">ICorDebugBreakpoint – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ea2d1-102">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="ea2d1-103">Představuje zarážku ve funkci nebo bod sledování na hodnotě.</span><span class="sxs-lookup"><span data-stu-id="ea2d1-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ea2d1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ea2d1-104">Methods</span></span>  
  
|<span data-ttu-id="ea2d1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ea2d1-105">Method</span></span>|<span data-ttu-id="ea2d1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ea2d1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ea2d1-107">Activate – metoda</span><span class="sxs-lookup"><span data-stu-id="ea2d1-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="ea2d1-108">Nastaví aktivní stav této `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="ea2d1-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="ea2d1-109">IsActive – metoda</span><span class="sxs-lookup"><span data-stu-id="ea2d1-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="ea2d1-110">Načte hodnotu, která označuje, zda `ICorDebugBreakpoint` je tato hodnota aktivní.</span><span class="sxs-lookup"><span data-stu-id="ea2d1-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea2d1-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ea2d1-111">Remarks</span></span>  
 <span data-ttu-id="ea2d1-112">Zarážky přímo nepodporují podmíněné výrazy.</span><span class="sxs-lookup"><span data-stu-id="ea2d1-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="ea2d1-113">Pokud jsou takové funkce žádoucí, ladicí program je musí implementovat nad `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="ea2d1-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="ea2d1-114">Rozhraní ICorDebugFunctionBreakpoint rozšiřuje `ICorDebugBreakpoint` na podporu zarážek v rámci funkcí.</span><span class="sxs-lookup"><span data-stu-id="ea2d1-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea2d1-115">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="ea2d1-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea2d1-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ea2d1-116">Requirements</span></span>  
 <span data-ttu-id="ea2d1-117">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea2d1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea2d1-118">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ea2d1-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea2d1-119">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea2d1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea2d1-120">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea2d1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea2d1-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea2d1-121">See also</span></span>

- [<span data-ttu-id="ea2d1-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ea2d1-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
