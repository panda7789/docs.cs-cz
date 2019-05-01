---
title: ICorDebugUnmanagedCallback – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback
helpviewer_keywords:
- ICorDebugUnmanagedCallback interface [.NET Framework debugging]
ms.assetid: bc71cbca-7d73-40e5-84dd-2109fade3c2a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60a1546068ae6a8c8be1c0af1ef3c7d770c23d70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993756"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="2bcb4-102">ICorDebugUnmanagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2bcb4-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="2bcb4-103">Poskytuje oznámení nativních událostí, které přímo nesouvisejí s common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="2bcb4-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2bcb4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2bcb4-104">Methods</span></span>  
  
|<span data-ttu-id="2bcb4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2bcb4-105">Method</span></span>|<span data-ttu-id="2bcb4-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2bcb4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2bcb4-107">DebugEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="2bcb4-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="2bcb4-108">Upozorní ladicího programu, že nativní události byl aktivován.</span><span class="sxs-lookup"><span data-stu-id="2bcb4-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bcb4-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2bcb4-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2bcb4-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="2bcb4-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bcb4-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2bcb4-111">Requirements</span></span>  
 <span data-ttu-id="2bcb4-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bcb4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bcb4-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2bcb4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2bcb4-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2bcb4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bcb4-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bcb4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bcb4-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2bcb4-116">See also</span></span>

- [<span data-ttu-id="2bcb4-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2bcb4-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
