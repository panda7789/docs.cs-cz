---
title: ICorDebugThread4 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugThread4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4
helpviewer_keywords:
- ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f213a35a12bfb5cc92558a76e122a1494d567f93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987048"
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="c6095-102">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6095-102">ICorDebugThread4 Interface</span></span>
<span data-ttu-id="c6095-103">Poskytuje informace o blokování vlákna.</span><span class="sxs-lookup"><span data-stu-id="c6095-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c6095-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c6095-104">Methods</span></span>  
  
|<span data-ttu-id="c6095-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c6095-105">Method</span></span>|<span data-ttu-id="c6095-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c6095-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c6095-107">GetBlockingObjects – metoda</span><span class="sxs-lookup"><span data-stu-id="c6095-107">GetBlockingObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="c6095-108">Poskytuje seřazený výčet [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) vlákna struktury, které poskytují informace o blokování.</span><span class="sxs-lookup"><span data-stu-id="c6095-108">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="c6095-109">HadUnhandledException – metoda</span><span class="sxs-lookup"><span data-stu-id="c6095-109">HadUnhandledException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="c6095-110">Určuje, zda vlákna někdy došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="c6095-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="c6095-111">GetCurrentCustomDebuggerNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="c6095-111">GetCurrentCustomDebuggerNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="c6095-112">Získá aktuální [icordebugmanagedcallback3::customnotification –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) objektu v aktuálním vláknu.</span><span class="sxs-lookup"><span data-stu-id="c6095-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6095-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6095-113">Remarks</span></span>  
 <span data-ttu-id="c6095-114">Toto rozhraní je logickým rozšířením ICorDebugThread icordebugthread2 –, a [icordebugthread3 –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c6095-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6095-115">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="c6095-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6095-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6095-116">Requirements</span></span>  
 <span data-ttu-id="c6095-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6095-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6095-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6095-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6095-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6095-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6095-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6095-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6095-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6095-121">See also</span></span>

- [<span data-ttu-id="c6095-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c6095-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c6095-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="c6095-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
