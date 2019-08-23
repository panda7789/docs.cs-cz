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
ms.openlocfilehash: 5d66a1aed1936d0146d42c8e4a5ad06dfa39c802
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962965"
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="8f95d-102">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f95d-102">ICorDebugThread4 Interface</span></span>
<span data-ttu-id="8f95d-103">Poskytuje informace o blokování vlákna.</span><span class="sxs-lookup"><span data-stu-id="8f95d-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8f95d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8f95d-104">Methods</span></span>  
  
|<span data-ttu-id="8f95d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8f95d-105">Method</span></span>|<span data-ttu-id="8f95d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8f95d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8f95d-107">GetBlockingObjects – metoda</span><span class="sxs-lookup"><span data-stu-id="8f95d-107">GetBlockingObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="8f95d-108">Poskytuje seřazený výčet struktur [CorDebugBlockingObject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) , které poskytují informace o blokování vláken.</span><span class="sxs-lookup"><span data-stu-id="8f95d-108">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="8f95d-109">HadUnhandledException – metoda</span><span class="sxs-lookup"><span data-stu-id="8f95d-109">HadUnhandledException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="8f95d-110">Označuje, zda má vlákno někdy neošetřenou výjimku.</span><span class="sxs-lookup"><span data-stu-id="8f95d-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="8f95d-111">GetCurrentCustomDebuggerNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="8f95d-111">GetCurrentCustomDebuggerNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="8f95d-112">Získá aktuální objekt [ICorDebugManagedCallback3 –:: CustomNotification –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="8f95d-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f95d-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8f95d-113">Remarks</span></span>  
 <span data-ttu-id="8f95d-114">Toto rozhraní je logické rozšíření rozhraní ICorDebugThread, ICorDebugThread2 a [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8f95d-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8f95d-115">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="8f95d-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f95d-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8f95d-116">Requirements</span></span>  
 <span data-ttu-id="8f95d-117">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f95d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f95d-118">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8f95d-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f95d-119">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f95d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f95d-120">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f95d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f95d-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8f95d-121">See also</span></span>

- [<span data-ttu-id="8f95d-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8f95d-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8f95d-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="8f95d-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
