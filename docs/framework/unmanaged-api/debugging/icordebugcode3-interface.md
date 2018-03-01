---
title: "ICorDebugCode3 – rozhraní"
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
- ICorDebugCode3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3
helpviewer_keywords:
- ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a89bc2b516f87a4deb7ccb794b5ae0352d6a8efc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="50e34-102">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50e34-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="50e34-103">Poskytne metodu, která rozšiřuje "ICorDebugCode" a "Icordebugcode2 –" k zadání informací o spravovaných návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="50e34-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="50e34-104">Metody</span><span class="sxs-lookup"><span data-stu-id="50e34-104">Methods</span></span>  
  
|<span data-ttu-id="50e34-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="50e34-105">Method</span></span>|<span data-ttu-id="50e34-106">Popis</span><span class="sxs-lookup"><span data-stu-id="50e34-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="50e34-107">GetReturnValueLiveOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="50e34-107">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="50e34-108">Pro zadaný korekce IL získá nativní posuny, kde má být umístěn zarážku tak, aby ladicí program můžete získat návratovou hodnotou z funkce.</span><span class="sxs-lookup"><span data-stu-id="50e34-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50e34-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="50e34-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50e34-110">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="50e34-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50e34-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="50e34-111">Requirements</span></span>  
 <span data-ttu-id="50e34-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50e34-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50e34-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50e34-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50e34-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50e34-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50e34-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50e34-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50e34-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="50e34-116">See Also</span></span>  
    
    
    
 [<span data-ttu-id="50e34-117">ICorDebugILFrame3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50e34-117">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 [<span data-ttu-id="50e34-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="50e34-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
