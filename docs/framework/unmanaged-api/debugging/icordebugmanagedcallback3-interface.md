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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108274"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="96a60-102">ICorDebugManagedCallback3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96a60-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="96a60-103">Poskytuje metodu zpětného volání, která určuje, že povolené vlastní oznámení ladicího programu bylo vyvoláno.</span><span class="sxs-lookup"><span data-stu-id="96a60-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="96a60-104">Metody</span><span class="sxs-lookup"><span data-stu-id="96a60-104">Methods</span></span>  
  
|<span data-ttu-id="96a60-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="96a60-105">Method</span></span>|<span data-ttu-id="96a60-106">Popis</span><span class="sxs-lookup"><span data-stu-id="96a60-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="96a60-107">CustomNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="96a60-107">CustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="96a60-108">Označuje, že povolené vlastní oznámení ladicího programu bylo vyvoláno.</span><span class="sxs-lookup"><span data-stu-id="96a60-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96a60-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96a60-109">Remarks</span></span>  
 <span data-ttu-id="96a60-110">Toto rozhraní je logickým rozšířením [icordebugmanagedcallback –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) a [icordebugmanagedcallback2 –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="96a60-110">This interface is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96a60-111">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="96a60-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96a60-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="96a60-112">Requirements</span></span>  
 <span data-ttu-id="96a60-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96a60-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96a60-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96a60-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96a60-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96a60-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="96a60-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="96a60-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="96a60-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96a60-117">See also</span></span>

- [<span data-ttu-id="96a60-118">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96a60-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="96a60-119">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96a60-119">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="96a60-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96a60-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="96a60-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="96a60-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
