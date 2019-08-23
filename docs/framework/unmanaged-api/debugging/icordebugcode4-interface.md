---
title: ICorDebugCode4 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugCode4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4
helpviewer_keywords:
- ICorDebugCode4 interface [.NET Framework debugging]
ms.assetid: a3fdf523-274a-449c-920b-9fcb0aed1d97
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ec40de7fe9e12315987e65e48f1727f5d5b80ef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960732"
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="0b4c9-102">ICorDebugCode4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b4c9-102">ICorDebugCode4 Interface</span></span>
<span data-ttu-id="0b4c9-103">Poskytuje metodu, která umožňuje ladicímu programu vytvořit výčet místních proměnných a argumentů ve funkci.</span><span class="sxs-lookup"><span data-stu-id="0b4c9-103">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0b4c9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0b4c9-104">Methods</span></span>  
  
|<span data-ttu-id="0b4c9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0b4c9-105">Method</span></span>|<span data-ttu-id="0b4c9-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0b4c9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0b4c9-107">EnumerateVariableHomes – metoda</span><span class="sxs-lookup"><span data-stu-id="0b4c9-107">EnumerateVariableHomes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="0b4c9-108">Získá enumerátor pro místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="0b4c9-108">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b4c9-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b4c9-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0b4c9-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="0b4c9-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b4c9-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0b4c9-111">Requirements</span></span>  
 <span data-ttu-id="0b4c9-112">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b4c9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b4c9-113">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0b4c9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b4c9-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b4c9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b4c9-115">**Verze .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b4c9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b4c9-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b4c9-116">See also</span></span>

- [<span data-ttu-id="0b4c9-117">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b4c9-117">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="0b4c9-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0b4c9-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
