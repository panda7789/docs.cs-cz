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
ms.openlocfilehash: 0bb25d060853abb20316a344bae3755b2f8b4dc7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791339"
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="4edb1-102">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4edb1-102">ICorDebugThread4 Interface</span></span>
<span data-ttu-id="4edb1-103">Poskytuje informace o blokování vlákna.</span><span class="sxs-lookup"><span data-stu-id="4edb1-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4edb1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4edb1-104">Methods</span></span>  
  
|<span data-ttu-id="4edb1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4edb1-105">Method</span></span>|<span data-ttu-id="4edb1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="4edb1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4edb1-107">GetBlockingObjects – metoda</span><span class="sxs-lookup"><span data-stu-id="4edb1-107">GetBlockingObjects Method</span></span>](icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="4edb1-108">Poskytuje seřazený výčet struktur [CorDebugBlockingObject –](cordebugblockingobject-structure.md) , které poskytují informace o blokování vláken.</span><span class="sxs-lookup"><span data-stu-id="4edb1-108">Provides an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="4edb1-109">HadUnhandledException – metoda</span><span class="sxs-lookup"><span data-stu-id="4edb1-109">HadUnhandledException Method</span></span>](icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="4edb1-110">Označuje, zda má vlákno někdy neošetřenou výjimku.</span><span class="sxs-lookup"><span data-stu-id="4edb1-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="4edb1-111">GetCurrentCustomDebuggerNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="4edb1-111">GetCurrentCustomDebuggerNotification Method</span></span>](icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="4edb1-112">Získá aktuální objekt [ICorDebugManagedCallback3 –:: CustomNotification –](icordebugmanagedcallback3-customnotification-method.md) v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="4edb1-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4edb1-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4edb1-113">Remarks</span></span>  
 <span data-ttu-id="4edb1-114">Toto rozhraní je logické rozšíření rozhraní ICorDebugThread, ICorDebugThread2 a [ICorDebugThread3](icordebugthread3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="4edb1-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4edb1-115">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="4edb1-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4edb1-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4edb1-116">Requirements</span></span>  
 <span data-ttu-id="4edb1-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4edb1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4edb1-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4edb1-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4edb1-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4edb1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4edb1-120">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4edb1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4edb1-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4edb1-121">See also</span></span>

- [<span data-ttu-id="4edb1-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="4edb1-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4edb1-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="4edb1-123">Debugging</span></span>](index.md)
