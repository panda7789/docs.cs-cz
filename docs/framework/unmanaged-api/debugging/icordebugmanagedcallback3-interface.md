---
title: ICorDebugManagedCallback3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3
helpviewer_keywords:
- ICorDebugManagedCallback3 interface [.NET Framework debugging]
ms.assetid: a95389d3-cf2e-47a4-9805-61426acc6b65
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 138ac80a9abb64d4c004e83e53ed1eea2b124ff2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909900"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="8f399-102">ICorDebugManagedCallback3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f399-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="8f399-103">Poskytuje metodu zpětného volání, která určuje, že povolené vlastní oznámení ladicího programu bylo vyvoláno.</span><span class="sxs-lookup"><span data-stu-id="8f399-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8f399-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8f399-104">Methods</span></span>  
  
|<span data-ttu-id="8f399-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8f399-105">Method</span></span>|<span data-ttu-id="8f399-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8f399-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8f399-107">CustomNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="8f399-107">CustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="8f399-108">Indikuje, že se aktivovalo oznámení o povoleném vlastním ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="8f399-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f399-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8f399-109">Remarks</span></span>  
 <span data-ttu-id="8f399-110">Toto rozhraní je logické rozšíření rozhraní [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) a [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8f399-110">This interface is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8f399-111">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="8f399-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f399-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8f399-112">Requirements</span></span>  
 <span data-ttu-id="8f399-113">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f399-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f399-114">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8f399-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f399-115">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f399-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f399-116">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f399-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f399-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8f399-117">See also</span></span>

- [<span data-ttu-id="8f399-118">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f399-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="8f399-119">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f399-119">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="8f399-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8f399-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8f399-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="8f399-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
