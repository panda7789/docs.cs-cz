---
title: ICorDebugModuleBreakpoint – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint
helpviewer_keywords:
- ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: 34667162-f314-475f-ae1b-ce9cb0fcbb83
topic_type:
- apiref
ms.openlocfilehash: 2bc5c21d2e1256d0e79390bea10aafcdefbed0d3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110340"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="d20e8-102">ICorDebugModuleBreakpoint – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d20e8-102">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="d20e8-103">Poskytuje přístup ke konkrétním modulům.</span><span class="sxs-lookup"><span data-stu-id="d20e8-103">Provides access to specific modules.</span></span> <span data-ttu-id="d20e8-104">Toto rozhraní je podtřídou rozhraní ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="d20e8-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d20e8-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d20e8-105">Methods</span></span>  
  
|<span data-ttu-id="d20e8-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="d20e8-106">Method</span></span>|<span data-ttu-id="d20e8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d20e8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d20e8-108">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="d20e8-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="d20e8-109">Získá ukazatel rozhraní na objekt ICorDebugModule, který odkazuje na modul, ve kterém je tato zarážka nastavena.</span><span class="sxs-lookup"><span data-stu-id="d20e8-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d20e8-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d20e8-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d20e8-111">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="d20e8-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d20e8-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d20e8-112">Requirements</span></span>  
 <span data-ttu-id="d20e8-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d20e8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d20e8-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d20e8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d20e8-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d20e8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d20e8-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d20e8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d20e8-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d20e8-117">See also</span></span>

- [<span data-ttu-id="d20e8-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d20e8-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
