---
title: "Rozhraní ICorDebugProcess8"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7ab1a70f-ec11-46ff-8869-cd8ca679cc51
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2985352cf8b209e98f749fbe40170e49014c9d9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess8-interface"></a><span data-ttu-id="f7401-102">Rozhraní ICorDebugProcess8</span><span class="sxs-lookup"><span data-stu-id="f7401-102">ICorDebugProcess8 Interface</span></span>
<span data-ttu-id="f7401-103">[V podporované [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] a novější verze]</span><span class="sxs-lookup"><span data-stu-id="f7401-103">[Supported in the [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="f7401-104">Logicky rozšiřuje rozhraní ICorDebugProcess k povolení nebo zakázání určitých typů [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) zpětná volání výjimek.</span><span class="sxs-lookup"><span data-stu-id="f7401-104">Logically extends the ICorDebugProcess interface to enable or disable certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f7401-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f7401-105">Methods</span></span>  
  
|<span data-ttu-id="f7401-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="f7401-106">Method</span></span>|<span data-ttu-id="f7401-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f7401-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f7401-108">EnableExceptionCallbacksOutsideOfMyCode – metoda</span><span class="sxs-lookup"><span data-stu-id="f7401-108">EnableExceptionCallbacksOutsideOfMyCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-enableexceptioncallbacksoutsideofmycode-method.md)|<span data-ttu-id="f7401-109">Povolí nebo zakáže určité typy [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) zpětná volání výjimek.</span><span class="sxs-lookup"><span data-stu-id="f7401-109">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7401-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f7401-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7401-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7401-111">Requirements</span></span>  
 <span data-ttu-id="f7401-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7401-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7401-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7401-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7401-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7401-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7401-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7401-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7401-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7401-116">See Also</span></span>  
 [<span data-ttu-id="f7401-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f7401-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f7401-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="f7401-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
