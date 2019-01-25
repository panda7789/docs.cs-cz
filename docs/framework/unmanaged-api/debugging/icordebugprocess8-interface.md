---
title: Rozhraní ICorDebugProcess8
ms.date: 03/30/2017
ms.assetid: 7ab1a70f-ec11-46ff-8869-cd8ca679cc51
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47ee7cae6f226993b0366ba34afa853e432e2e50
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547982"
---
# <a name="icordebugprocess8-interface"></a><span data-ttu-id="ad1eb-102">Rozhraní ICorDebugProcess8</span><span class="sxs-lookup"><span data-stu-id="ad1eb-102">ICorDebugProcess8 Interface</span></span>
<span data-ttu-id="ad1eb-103">[Podporované v [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] a novější verze]</span><span class="sxs-lookup"><span data-stu-id="ad1eb-103">[Supported in the [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="ad1eb-104">Logicky rozšiřuje icordebugprocess – rozhraní pro povolení nebo zakázání určitých typů [icordebugmanagedcallback2 –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) zpětných volání výjimky.</span><span class="sxs-lookup"><span data-stu-id="ad1eb-104">Logically extends the ICorDebugProcess interface to enable or disable certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ad1eb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ad1eb-105">Methods</span></span>  
  
|<span data-ttu-id="ad1eb-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="ad1eb-106">Method</span></span>|<span data-ttu-id="ad1eb-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ad1eb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ad1eb-108">EnableExceptionCallbacksOutsideOfMyCode – metoda</span><span class="sxs-lookup"><span data-stu-id="ad1eb-108">EnableExceptionCallbacksOutsideOfMyCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-enableexceptioncallbacksoutsideofmycode-method.md)|<span data-ttu-id="ad1eb-109">Povolí nebo zakáže určité typy [icordebugmanagedcallback2 –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) zpětných volání výjimky.</span><span class="sxs-lookup"><span data-stu-id="ad1eb-109">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad1eb-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad1eb-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad1eb-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad1eb-111">Requirements</span></span>  
 <span data-ttu-id="ad1eb-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad1eb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad1eb-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad1eb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad1eb-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad1eb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad1eb-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad1eb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad1eb-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad1eb-116">See also</span></span>
- [<span data-ttu-id="ad1eb-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ad1eb-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ad1eb-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="ad1eb-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
