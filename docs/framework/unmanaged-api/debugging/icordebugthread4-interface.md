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
ms.openlocfilehash: 8779dbc95a8bef13d45605295bd68b1d3f16851d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122433"
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="6ce08-102">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6ce08-102">ICorDebugThread4 Interface</span></span>
<span data-ttu-id="6ce08-103">Poskytuje informace o blokování vlákna.</span><span class="sxs-lookup"><span data-stu-id="6ce08-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6ce08-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6ce08-104">Methods</span></span>  
  
|<span data-ttu-id="6ce08-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6ce08-105">Method</span></span>|<span data-ttu-id="6ce08-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6ce08-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6ce08-107">GetBlockingObjects – metoda</span><span class="sxs-lookup"><span data-stu-id="6ce08-107">GetBlockingObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="6ce08-108">Poskytuje seřazený výčet struktur [CorDebugBlockingObject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) , které poskytují informace o blokování vláken.</span><span class="sxs-lookup"><span data-stu-id="6ce08-108">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="6ce08-109">HadUnhandledException – metoda</span><span class="sxs-lookup"><span data-stu-id="6ce08-109">HadUnhandledException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="6ce08-110">Označuje, zda má vlákno někdy neošetřenou výjimku.</span><span class="sxs-lookup"><span data-stu-id="6ce08-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="6ce08-111">GetCurrentCustomDebuggerNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="6ce08-111">GetCurrentCustomDebuggerNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="6ce08-112">Získá aktuální objekt [ICorDebugManagedCallback3 –:: CustomNotification –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="6ce08-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ce08-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ce08-113">Remarks</span></span>  
 <span data-ttu-id="6ce08-114">Toto rozhraní je logické rozšíření rozhraní ICorDebugThread, ICorDebugThread2 a [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="6ce08-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ce08-115">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="6ce08-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ce08-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6ce08-116">Requirements</span></span>  
 <span data-ttu-id="6ce08-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ce08-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ce08-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6ce08-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ce08-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6ce08-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ce08-120">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ce08-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ce08-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ce08-121">See also</span></span>

- [<span data-ttu-id="6ce08-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6ce08-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6ce08-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="6ce08-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
