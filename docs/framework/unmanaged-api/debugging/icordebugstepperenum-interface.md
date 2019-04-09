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
ms.openlocfilehash: 89552a099241f1bec61f9aa8a8321ef9932e886c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173222"
---
# <a name="icordebugstepperenum-interface"></a><span data-ttu-id="9447d-102">ICorDebugStepperEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9447d-102">ICorDebugStepperEnum Interface</span></span>
<span data-ttu-id="9447d-103">Implementuje metody ICorDebugEnum a vytváří výčet polí icordebugstepper –.</span><span class="sxs-lookup"><span data-stu-id="9447d-103">Implements ICorDebugEnum methods, and enumerates ICorDebugStepper arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9447d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9447d-104">Methods</span></span>  
  
|<span data-ttu-id="9447d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9447d-105">Method</span></span>|<span data-ttu-id="9447d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9447d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9447d-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="9447d-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-next-method.md)|<span data-ttu-id="9447d-108">Získá zadaný počet `ICorDebugStepper` instancí z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="9447d-108">Gets the specified number of `ICorDebugStepper` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9447d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9447d-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9447d-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="9447d-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9447d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9447d-111">Requirements</span></span>  
 <span data-ttu-id="9447d-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9447d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9447d-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9447d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9447d-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9447d-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9447d-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9447d-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9447d-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9447d-116">See also</span></span>

- [<span data-ttu-id="9447d-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9447d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
