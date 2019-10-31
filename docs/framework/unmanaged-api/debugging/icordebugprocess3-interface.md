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
ms.openlocfilehash: 5e2d68d1e2dcaa656df4e35b135eeaf522878c6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137132"
---
# <a name="icordebugprocess3-interface"></a><span data-ttu-id="736c4-102">ICorDebugProcess3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="736c4-102">ICorDebugProcess3 Interface</span></span>
<span data-ttu-id="736c4-103">Řídí vlastní oznámení ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="736c4-103">Controls custom debugger notifications.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="736c4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="736c4-104">Methods</span></span>  
  
|<span data-ttu-id="736c4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="736c4-105">Method</span></span>|<span data-ttu-id="736c4-106">Popis</span><span class="sxs-lookup"><span data-stu-id="736c4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="736c4-107">SetEnableCustomNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="736c4-107">SetEnableCustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md)|<span data-ttu-id="736c4-108">Povolí nebo zakáže oznámení vlastního ladicího programu určeného typu.</span><span class="sxs-lookup"><span data-stu-id="736c4-108">Enables and disables custom debugger notifications of the specified type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="736c4-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="736c4-109">Remarks</span></span>  
 <span data-ttu-id="736c4-110">Toto rozhraní logicky rozšiřuje rozhraní ICorDebugProcess a ICorDebugProcess2.</span><span class="sxs-lookup"><span data-stu-id="736c4-110">This interface logically extends the ICorDebugProcess and ICorDebugProcess2 interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="736c4-111">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="736c4-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="736c4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="736c4-112">Requirements</span></span>  
 <span data-ttu-id="736c4-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="736c4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="736c4-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="736c4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="736c4-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="736c4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="736c4-116">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="736c4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="736c4-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="736c4-117">See also</span></span>

- [<span data-ttu-id="736c4-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="736c4-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="736c4-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="736c4-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
