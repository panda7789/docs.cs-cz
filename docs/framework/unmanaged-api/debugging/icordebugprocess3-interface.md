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
ms.openlocfilehash: 28d1d426276e9654c2122f03fb64735b7e67f44f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792473"
---
# <a name="icordebugprocess3-interface"></a><span data-ttu-id="db187-102">ICorDebugProcess3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db187-102">ICorDebugProcess3 Interface</span></span>
<span data-ttu-id="db187-103">Řídí vlastní oznámení ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="db187-103">Controls custom debugger notifications.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="db187-104">Metody</span><span class="sxs-lookup"><span data-stu-id="db187-104">Methods</span></span>  
  
|<span data-ttu-id="db187-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="db187-105">Method</span></span>|<span data-ttu-id="db187-106">Popis</span><span class="sxs-lookup"><span data-stu-id="db187-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="db187-107">SetEnableCustomNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="db187-107">SetEnableCustomNotification Method</span></span>](icordebugprocess3-setenablecustomnotification-method.md)|<span data-ttu-id="db187-108">Povolí nebo zakáže oznámení vlastního ladicího programu určeného typu.</span><span class="sxs-lookup"><span data-stu-id="db187-108">Enables and disables custom debugger notifications of the specified type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db187-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db187-109">Remarks</span></span>  
 <span data-ttu-id="db187-110">Toto rozhraní logicky rozšiřuje rozhraní ICorDebugProcess a ICorDebugProcess2.</span><span class="sxs-lookup"><span data-stu-id="db187-110">This interface logically extends the ICorDebugProcess and ICorDebugProcess2 interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="db187-111">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="db187-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db187-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db187-112">Requirements</span></span>  
 <span data-ttu-id="db187-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db187-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db187-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="db187-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db187-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="db187-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db187-116">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db187-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db187-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db187-117">See also</span></span>

- [<span data-ttu-id="db187-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="db187-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="db187-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="db187-119">Debugging</span></span>](index.md)
