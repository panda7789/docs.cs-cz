---
title: ICorDebugProcessEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum
helpviewer_keywords:
- ICorDebugProcessEnum interface [.NET Framework debugging]
ms.assetid: b63a507a-ca97-4be0-8e4f-401cce2125f6
topic_type:
- apiref
ms.openlocfilehash: 9f5406c35915e447831d233804413034a429e8a1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139774"
---
# <a name="icordebugprocessenum-interface"></a><span data-ttu-id="35a57-102">ICorDebugProcessEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="35a57-102">ICorDebugProcessEnum Interface</span></span>
<span data-ttu-id="35a57-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugProcess.</span><span class="sxs-lookup"><span data-stu-id="35a57-103">Implements ICorDebugEnum methods and enumerates ICorDebugProcess arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="35a57-104">Metody</span><span class="sxs-lookup"><span data-stu-id="35a57-104">Methods</span></span>  
  
|<span data-ttu-id="35a57-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="35a57-105">Method</span></span>|<span data-ttu-id="35a57-106">Popis</span><span class="sxs-lookup"><span data-stu-id="35a57-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="35a57-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="35a57-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-next-method.md)|<span data-ttu-id="35a57-108">Získá zadaný počet instancí `ICorDebugProcess` z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="35a57-108">Gets the specified number of `ICorDebugProcess` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35a57-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="35a57-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35a57-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="35a57-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35a57-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="35a57-111">Requirements</span></span>  
 <span data-ttu-id="35a57-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35a57-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35a57-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="35a57-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35a57-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="35a57-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35a57-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35a57-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35a57-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="35a57-116">See also</span></span>

- [<span data-ttu-id="35a57-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="35a57-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
