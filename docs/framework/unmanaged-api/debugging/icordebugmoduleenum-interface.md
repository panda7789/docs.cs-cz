---
title: ICorDebugModuleEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum
helpviewer_keywords:
- ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 2fb93cd6-6d47-4fdc-a9a0-047726fd03a1
topic_type:
- apiref
ms.openlocfilehash: b019c198635373fa6aaea01914dc9747b7486ae0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792883"
---
# <a name="icordebugmoduleenum-interface"></a><span data-ttu-id="7ea64-102">ICorDebugModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ea64-102">ICorDebugModuleEnum Interface</span></span>

<span data-ttu-id="7ea64-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="7ea64-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7ea64-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7ea64-104">Methods</span></span>  
  
|<span data-ttu-id="7ea64-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7ea64-105">Method</span></span>|<span data-ttu-id="7ea64-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7ea64-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7ea64-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="7ea64-107">Next Method</span></span>](icordebugmoduleenum-next-method.md)|<span data-ttu-id="7ea64-108">Získá zadaný počet instancí `ICorDebugModule` z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="7ea64-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ea64-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7ea64-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ea64-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="7ea64-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ea64-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ea64-111">Requirements</span></span>  
 <span data-ttu-id="7ea64-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ea64-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ea64-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7ea64-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ea64-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7ea64-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ea64-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ea64-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ea64-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ea64-116">See also</span></span>

- [<span data-ttu-id="7ea64-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7ea64-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
