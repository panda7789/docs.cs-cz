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
ms.openlocfilehash: b97f29b94ed4fad6892697ca1c7ed4a20c99c03e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793269"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="f69ee-102">ICorDebugManagedCallback3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f69ee-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="f69ee-103">Poskytuje metodu zpětného volání, která určuje, že povolené vlastní oznámení ladicího programu bylo vyvoláno.</span><span class="sxs-lookup"><span data-stu-id="f69ee-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f69ee-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f69ee-104">Methods</span></span>  
  
|<span data-ttu-id="f69ee-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f69ee-105">Method</span></span>|<span data-ttu-id="f69ee-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f69ee-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f69ee-107">CustomNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="f69ee-107">CustomNotification Method</span></span>](icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="f69ee-108">Indikuje, že se aktivovalo oznámení o povoleném vlastním ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="f69ee-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f69ee-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f69ee-109">Remarks</span></span>  
 <span data-ttu-id="f69ee-110">Toto rozhraní je logické rozšíření rozhraní [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) a [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f69ee-110">This interface is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f69ee-111">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="f69ee-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f69ee-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f69ee-112">Requirements</span></span>  
 <span data-ttu-id="f69ee-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f69ee-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f69ee-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f69ee-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f69ee-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f69ee-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f69ee-116">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f69ee-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f69ee-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f69ee-117">See also</span></span>

- [<span data-ttu-id="f69ee-118">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f69ee-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="f69ee-119">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f69ee-119">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="f69ee-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f69ee-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f69ee-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="f69ee-121">Debugging</span></span>](index.md)
