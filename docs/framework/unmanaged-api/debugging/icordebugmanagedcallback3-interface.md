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
ms.openlocfilehash: acab49097059081540ec364d7f134d31432988a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723254"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="383fc-102">ICorDebugManagedCallback3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="383fc-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="383fc-103">Poskytuje metodu zpětného volání, která určuje, že povolené vlastní oznámení ladicího programu bylo vyvoláno.</span><span class="sxs-lookup"><span data-stu-id="383fc-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="383fc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="383fc-104">Methods</span></span>  
  
|<span data-ttu-id="383fc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="383fc-105">Method</span></span>|<span data-ttu-id="383fc-106">Popis</span><span class="sxs-lookup"><span data-stu-id="383fc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="383fc-107">CustomNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="383fc-107">CustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="383fc-108">Označuje, že povolené vlastní oznámení ladicího programu bylo vyvoláno.</span><span class="sxs-lookup"><span data-stu-id="383fc-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="383fc-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="383fc-109">Remarks</span></span>  
 <span data-ttu-id="383fc-110">Toto rozhraní je logickým rozšířením [icordebugmanagedcallback –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) a [icordebugmanagedcallback2 –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="383fc-110">This interface is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="383fc-111">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="383fc-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="383fc-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="383fc-112">Requirements</span></span>  
 <span data-ttu-id="383fc-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="383fc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="383fc-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="383fc-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="383fc-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="383fc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="383fc-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="383fc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="383fc-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="383fc-117">See also</span></span>

- [<span data-ttu-id="383fc-118">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="383fc-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="383fc-119">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="383fc-119">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="383fc-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="383fc-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="383fc-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="383fc-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
