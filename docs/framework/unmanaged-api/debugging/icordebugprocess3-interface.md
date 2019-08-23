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
ms.openlocfilehash: 05900f55885f8f3a4c470d6842c42d0fc3e0171e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957445"
---
# <a name="icordebugprocess3-interface"></a><span data-ttu-id="6a1e0-102">ICorDebugProcess3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a1e0-102">ICorDebugProcess3 Interface</span></span>
<span data-ttu-id="6a1e0-103">Řídí vlastní oznámení ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="6a1e0-103">Controls custom debugger notifications.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6a1e0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6a1e0-104">Methods</span></span>  
  
|<span data-ttu-id="6a1e0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6a1e0-105">Method</span></span>|<span data-ttu-id="6a1e0-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6a1e0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6a1e0-107">SetEnableCustomNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="6a1e0-107">SetEnableCustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md)|<span data-ttu-id="6a1e0-108">Povolí nebo zakáže oznámení vlastního ladicího programu určeného typu.</span><span class="sxs-lookup"><span data-stu-id="6a1e0-108">Enables and disables custom debugger notifications of the specified type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a1e0-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a1e0-109">Remarks</span></span>  
 <span data-ttu-id="6a1e0-110">Toto rozhraní logicky rozšiřuje rozhraní ICorDebugProcess a ICorDebugProcess2.</span><span class="sxs-lookup"><span data-stu-id="6a1e0-110">This interface logically extends the ICorDebugProcess and ICorDebugProcess2 interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a1e0-111">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="6a1e0-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a1e0-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a1e0-112">Requirements</span></span>  
 <span data-ttu-id="6a1e0-113">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a1e0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a1e0-114">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6a1e0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a1e0-115">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a1e0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a1e0-116">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a1e0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a1e0-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a1e0-117">See also</span></span>

- [<span data-ttu-id="6a1e0-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6a1e0-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6a1e0-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="6a1e0-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
