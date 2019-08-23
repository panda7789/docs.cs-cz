---
title: ICorDebugStepperEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugStepperEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepperEnum
helpviewer_keywords:
- ICorDebugStepperEnum interface [.NET Framework debugging]
ms.assetid: 988718c1-1a4a-40f2-a04c-7d67e5cfe1e2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7336f958019c2f696a9b1a26b075c076cfc84f5d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953022"
---
# <a name="icordebugstepperenum-interface"></a><span data-ttu-id="27235-102">ICorDebugStepperEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="27235-102">ICorDebugStepperEnum Interface</span></span>
<span data-ttu-id="27235-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugStepper.</span><span class="sxs-lookup"><span data-stu-id="27235-103">Implements ICorDebugEnum methods, and enumerates ICorDebugStepper arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="27235-104">Metody</span><span class="sxs-lookup"><span data-stu-id="27235-104">Methods</span></span>  
  
|<span data-ttu-id="27235-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="27235-105">Method</span></span>|<span data-ttu-id="27235-106">Popis</span><span class="sxs-lookup"><span data-stu-id="27235-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="27235-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="27235-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-next-method.md)|<span data-ttu-id="27235-108">Získá zadaný počet `ICorDebugStepper` instancí z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="27235-108">Gets the specified number of `ICorDebugStepper` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27235-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="27235-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="27235-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="27235-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27235-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="27235-111">Requirements</span></span>  
 <span data-ttu-id="27235-112">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27235-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27235-113">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="27235-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27235-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27235-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27235-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27235-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27235-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27235-116">See also</span></span>

- [<span data-ttu-id="27235-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="27235-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
