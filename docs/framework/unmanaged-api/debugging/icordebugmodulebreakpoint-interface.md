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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03616f2756830e180155102492b15e18fee1085c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965115"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="90450-102">ICorDebugModuleBreakpoint – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90450-102">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="90450-103">Poskytuje přístup ke konkrétním modulům.</span><span class="sxs-lookup"><span data-stu-id="90450-103">Provides access to specific modules.</span></span> <span data-ttu-id="90450-104">Toto rozhraní je podtřídou rozhraní ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="90450-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="90450-105">Metody</span><span class="sxs-lookup"><span data-stu-id="90450-105">Methods</span></span>  
  
|<span data-ttu-id="90450-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="90450-106">Method</span></span>|<span data-ttu-id="90450-107">Popis</span><span class="sxs-lookup"><span data-stu-id="90450-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="90450-108">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="90450-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="90450-109">Získá ukazatel rozhraní na objekt ICorDebugModule, který odkazuje na modul, ve kterém je tato zarážka nastavena.</span><span class="sxs-lookup"><span data-stu-id="90450-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90450-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90450-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90450-111">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="90450-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90450-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90450-112">Requirements</span></span>  
 <span data-ttu-id="90450-113">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90450-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90450-114">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="90450-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90450-115">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90450-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90450-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90450-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90450-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90450-117">See also</span></span>

- [<span data-ttu-id="90450-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="90450-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
