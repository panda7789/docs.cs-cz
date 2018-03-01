---
title: "ICorDebugProcess3 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 894d3295b83a1971792e6da845f276be486a4ea5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess3-interface"></a><span data-ttu-id="1d265-102">ICorDebugProcess3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1d265-102">ICorDebugProcess3 Interface</span></span>
<span data-ttu-id="1d265-103">Řídí vlastní oznámení ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="1d265-103">Controls custom debugger notifications.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1d265-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1d265-104">Methods</span></span>  
  
|<span data-ttu-id="1d265-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1d265-105">Method</span></span>|<span data-ttu-id="1d265-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1d265-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1d265-107">SetEnableCustomNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="1d265-107">SetEnableCustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md)|<span data-ttu-id="1d265-108">Povolí nebo zakáže oznámení vlastní ladicí program zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="1d265-108">Enables and disables custom debugger notifications of the specified type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d265-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1d265-109">Remarks</span></span>  
 <span data-ttu-id="1d265-110">Toto rozhraní logicky rozšiřuje ICorDebugProcess a icordebugprocess2 – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1d265-110">This interface logically extends the ICorDebugProcess and ICorDebugProcess2 interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d265-111">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="1d265-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d265-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1d265-112">Requirements</span></span>  
 <span data-ttu-id="1d265-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d265-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d265-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d265-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d265-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d265-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d265-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d265-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d265-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d265-117">See Also</span></span>  
 [<span data-ttu-id="1d265-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="1d265-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="1d265-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="1d265-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
