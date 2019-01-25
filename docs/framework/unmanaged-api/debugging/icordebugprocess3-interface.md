---
title: ICorDebugProcess3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3
helpviewer_keywords:
- ICorDebugProcess3 interface [.NET Framework debugging]
ms.assetid: ced9c82e-d7b0-4806-a151-98b6611d3097
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75dc379baf8d92b9b27bdb58ccab930c2d4f91e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709166"
---
# <a name="icordebugprocess3-interface"></a><span data-ttu-id="e7954-102">ICorDebugProcess3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e7954-102">ICorDebugProcess3 Interface</span></span>
<span data-ttu-id="e7954-103">Řídí vlastní oznámení ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="e7954-103">Controls custom debugger notifications.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e7954-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e7954-104">Methods</span></span>  
  
|<span data-ttu-id="e7954-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e7954-105">Method</span></span>|<span data-ttu-id="e7954-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e7954-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e7954-107">SetEnableCustomNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="e7954-107">SetEnableCustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md)|<span data-ttu-id="e7954-108">Povolí nebo zakáže vlastní oznámení ladicího programu zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="e7954-108">Enables and disables custom debugger notifications of the specified type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7954-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e7954-109">Remarks</span></span>  
 <span data-ttu-id="e7954-110">Toto rozhraní rozšiřuje logicky ICorDebugProcess a icordebugprocess2 – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e7954-110">This interface logically extends the ICorDebugProcess and ICorDebugProcess2 interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7954-111">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="e7954-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7954-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7954-112">Requirements</span></span>  
 <span data-ttu-id="e7954-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7954-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7954-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7954-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7954-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7954-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7954-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7954-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7954-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7954-117">See also</span></span>
- [<span data-ttu-id="e7954-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e7954-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e7954-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="e7954-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
