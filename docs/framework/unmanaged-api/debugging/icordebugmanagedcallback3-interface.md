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
ms.openlocfilehash: ab1dab753728102fc27e39c3ed64bf776e2e5ad5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634467"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="66770-102">ICorDebugManagedCallback3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66770-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="66770-103">Poskytuje metodu zpětného volání, která určuje, že povolené vlastní oznámení ladicího programu bylo vyvoláno.</span><span class="sxs-lookup"><span data-stu-id="66770-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="66770-104">Metody</span><span class="sxs-lookup"><span data-stu-id="66770-104">Methods</span></span>  
  
|<span data-ttu-id="66770-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="66770-105">Method</span></span>|<span data-ttu-id="66770-106">Popis</span><span class="sxs-lookup"><span data-stu-id="66770-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="66770-107">CustomNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="66770-107">CustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="66770-108">Označuje, že povolené vlastní oznámení ladicího programu bylo vyvoláno.</span><span class="sxs-lookup"><span data-stu-id="66770-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66770-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66770-109">Remarks</span></span>  
 <span data-ttu-id="66770-110">Toto rozhraní je logickým rozšířením [icordebugmanagedcallback –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) a [icordebugmanagedcallback2 –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="66770-110">This interface is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66770-111">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="66770-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66770-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66770-112">Requirements</span></span>  
 <span data-ttu-id="66770-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66770-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66770-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66770-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66770-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66770-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66770-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66770-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66770-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66770-117">See also</span></span>
- [<span data-ttu-id="66770-118">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66770-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="66770-119">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66770-119">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="66770-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="66770-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="66770-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="66770-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
