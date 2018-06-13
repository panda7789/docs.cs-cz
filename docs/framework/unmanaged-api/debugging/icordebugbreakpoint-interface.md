---
title: ICorDebugBreakpoint Interface1
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
ms.openlocfilehash: 220cd1a41ed69325b557e6498a511865b78817ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404512"
---
# <a name="icordebugbreakpoint-interface1"></a><span data-ttu-id="3c38c-102">ICorDebugBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="3c38c-102">ICorDebugBreakpoint Interface1</span></span>
<span data-ttu-id="3c38c-103">Představuje zarážka v funkci nebo bod sledovat na hodnotě.</span><span class="sxs-lookup"><span data-stu-id="3c38c-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3c38c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3c38c-104">Methods</span></span>  
  
|<span data-ttu-id="3c38c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3c38c-105">Method</span></span>|<span data-ttu-id="3c38c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3c38c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3c38c-107">Activate – metoda</span><span class="sxs-lookup"><span data-stu-id="3c38c-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="3c38c-108">Nastaví aktivní stav tohoto `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="3c38c-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="3c38c-109">IsActive – metoda</span><span class="sxs-lookup"><span data-stu-id="3c38c-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="3c38c-110">Získá hodnotu, která určuje, jestli to `ICorDebugBreakpoint` je aktivní.</span><span class="sxs-lookup"><span data-stu-id="3c38c-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c38c-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3c38c-111">Remarks</span></span>  
 <span data-ttu-id="3c38c-112">Zarážky přímo nepodporují podmíněné výrazy.</span><span class="sxs-lookup"><span data-stu-id="3c38c-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="3c38c-113">V případě potřeby tyto funkce ladicí program musí implementovat ho na `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="3c38c-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="3c38c-114">Rozšiřuje rozhraní ICorDebugFunctionBreakpoint `ICorDebugBreakpoint` pro podporu zarážky v rámci funkcí.</span><span class="sxs-lookup"><span data-stu-id="3c38c-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c38c-115">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="3c38c-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c38c-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3c38c-116">Requirements</span></span>  
 <span data-ttu-id="3c38c-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c38c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c38c-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c38c-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c38c-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c38c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c38c-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c38c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c38c-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c38c-121">See Also</span></span>  
 [<span data-ttu-id="3c38c-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="3c38c-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
