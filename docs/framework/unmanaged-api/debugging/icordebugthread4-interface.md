---
title: "ICorDebugThread4 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread4
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread4
helpviewer_keywords: ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e54611a38193a05a33381e798a61977d7aec41a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="c4430-102">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4430-102">ICorDebugThread4 Interface</span></span>
<span data-ttu-id="c4430-103">Poskytuje informace o blokování vlákna.</span><span class="sxs-lookup"><span data-stu-id="c4430-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c4430-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c4430-104">Methods</span></span>  
  
|<span data-ttu-id="c4430-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c4430-105">Method</span></span>|<span data-ttu-id="c4430-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c4430-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c4430-107">Getblockingobjects – metoda</span><span class="sxs-lookup"><span data-stu-id="c4430-107">GetBlockingObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="c4430-108">Poskytuje seřazený výčet [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) vláken struktury, které poskytují informace o blokování.</span><span class="sxs-lookup"><span data-stu-id="c4430-108">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="c4430-109">Hadunhandledexception – metoda</span><span class="sxs-lookup"><span data-stu-id="c4430-109">HadUnhandledException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="c4430-110">Určuje, zda vlákno někdy došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="c4430-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="c4430-111">Getcurrentcustomdebuggernotification – metoda</span><span class="sxs-lookup"><span data-stu-id="c4430-111">GetCurrentCustomDebuggerNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="c4430-112">Získá aktuální [icordebugmanagedcallback3::customnotification –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) objekt na aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="c4430-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4430-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4430-113">Remarks</span></span>  
 <span data-ttu-id="c4430-114">Toto rozhraní je logické rozšíření ICorDebugThread, icordebugthread2 –, a [icordebugthread3 –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c4430-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4430-115">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="c4430-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4430-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4430-116">Requirements</span></span>  
 <span data-ttu-id="c4430-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4430-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4430-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4430-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4430-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4430-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4430-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4430-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4430-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4430-121">See Also</span></span>  
 [<span data-ttu-id="c4430-122">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4430-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="c4430-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="c4430-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
