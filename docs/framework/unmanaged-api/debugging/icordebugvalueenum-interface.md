---
title: ICorDebugValueEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum
helpviewer_keywords:
- ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: 88989482-a09f-4bd0-9adb-16f47b0291fd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0aa7e5cfce67c2854f943f65909acb39cfc0d214
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913994"
---
# <a name="icordebugvalueenum-interface"></a><span data-ttu-id="f8f17-102">ICorDebugValueEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8f17-102">ICorDebugValueEnum Interface</span></span>
<span data-ttu-id="f8f17-103">Implementuje metody "ICorDebugEnum" a vytvoří výčet polí "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="f8f17-103">Implements "ICorDebugEnum" methods and enumerates "ICorDebugValue" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8f17-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f8f17-104">Methods</span></span>  
  
|<span data-ttu-id="f8f17-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f8f17-105">Method</span></span>|<span data-ttu-id="f8f17-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f8f17-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8f17-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="f8f17-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalueenum-next-method.md)|<span data-ttu-id="f8f17-108">Získá zadaný počet `ICorDebugValue` instancí z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="f8f17-108">Gets the specified number of `ICorDebugValue` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8f17-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f8f17-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8f17-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="f8f17-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8f17-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8f17-111">Requirements</span></span>  
 <span data-ttu-id="f8f17-112">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8f17-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8f17-113">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f8f17-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8f17-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8f17-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8f17-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8f17-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8f17-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8f17-116">See also</span></span>

- [<span data-ttu-id="f8f17-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f8f17-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
