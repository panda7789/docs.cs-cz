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
ms.openlocfilehash: 95c2218aadd62902ff9bc7f2e6a190aa2ce241ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418844"
---
# <a name="icordebugprocess3-interface"></a><span data-ttu-id="3a0af-102">ICorDebugProcess3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3a0af-102">ICorDebugProcess3 Interface</span></span>
<span data-ttu-id="3a0af-103">Řídí vlastní oznámení ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="3a0af-103">Controls custom debugger notifications.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3a0af-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3a0af-104">Methods</span></span>  
  
|<span data-ttu-id="3a0af-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3a0af-105">Method</span></span>|<span data-ttu-id="3a0af-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3a0af-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3a0af-107">SetEnableCustomNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="3a0af-107">SetEnableCustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md)|<span data-ttu-id="3a0af-108">Povolí nebo zakáže oznámení vlastní ladicí program zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="3a0af-108">Enables and disables custom debugger notifications of the specified type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a0af-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3a0af-109">Remarks</span></span>  
 <span data-ttu-id="3a0af-110">Toto rozhraní logicky rozšiřuje ICorDebugProcess a icordebugprocess2 – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3a0af-110">This interface logically extends the ICorDebugProcess and ICorDebugProcess2 interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a0af-111">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="3a0af-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a0af-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3a0af-112">Requirements</span></span>  
 <span data-ttu-id="3a0af-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a0af-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a0af-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3a0af-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a0af-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a0af-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a0af-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a0af-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a0af-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a0af-117">See Also</span></span>  
 [<span data-ttu-id="3a0af-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="3a0af-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="3a0af-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="3a0af-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
