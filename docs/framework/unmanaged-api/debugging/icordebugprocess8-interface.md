---
title: Rozhraní ICorDebugProcess8
ms.date: 03/30/2017
ms.assetid: 7ab1a70f-ec11-46ff-8869-cd8ca679cc51
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 349e0cf93a981a2c598d02f67978e524a6763728
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948574"
---
# <a name="icordebugprocess8-interface"></a><span data-ttu-id="30d1d-102">Rozhraní ICorDebugProcess8</span><span class="sxs-lookup"><span data-stu-id="30d1d-102">ICorDebugProcess8 Interface</span></span>
<span data-ttu-id="30d1d-103">[Podporované v [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] a novější verze]</span><span class="sxs-lookup"><span data-stu-id="30d1d-103">[Supported in the [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="30d1d-104">Logicky rozšiřuje icordebugprocess – rozhraní pro povolení nebo zakázání určitých typů [icordebugmanagedcallback2 –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) zpětných volání výjimky.</span><span class="sxs-lookup"><span data-stu-id="30d1d-104">Logically extends the ICorDebugProcess interface to enable or disable certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="30d1d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="30d1d-105">Methods</span></span>  
  
|<span data-ttu-id="30d1d-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="30d1d-106">Method</span></span>|<span data-ttu-id="30d1d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="30d1d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="30d1d-108">EnableExceptionCallbacksOutsideOfMyCode – metoda</span><span class="sxs-lookup"><span data-stu-id="30d1d-108">EnableExceptionCallbacksOutsideOfMyCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-enableexceptioncallbacksoutsideofmycode-method.md)|<span data-ttu-id="30d1d-109">Povolí nebo zakáže určité typy [icordebugmanagedcallback2 –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) zpětných volání výjimky.</span><span class="sxs-lookup"><span data-stu-id="30d1d-109">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30d1d-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30d1d-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30d1d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="30d1d-111">Requirements</span></span>  
 <span data-ttu-id="30d1d-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30d1d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30d1d-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30d1d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30d1d-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30d1d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30d1d-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30d1d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30d1d-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30d1d-116">See also</span></span>

- [<span data-ttu-id="30d1d-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="30d1d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="30d1d-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="30d1d-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
