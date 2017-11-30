---
title: "ICorDebugCode3 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode3
helpviewer_keywords: ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ee60d052c65df64b1a753166b301ba0012cdc8e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="e2990-102">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2990-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="e2990-103">Poskytne metodu, která rozšiřuje "ICorDebugCode" a "Icordebugcode2 –" k zadání informací o spravovaných návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e2990-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e2990-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e2990-104">Methods</span></span>  
  
|<span data-ttu-id="e2990-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e2990-105">Method</span></span>|<span data-ttu-id="e2990-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e2990-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e2990-107">Getreturnvalueliveoffset – metoda</span><span class="sxs-lookup"><span data-stu-id="e2990-107">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="e2990-108">Pro zadaný korekce IL získá nativní posuny, kde má být umístěn zarážku tak, aby ladicí program můžete získat návratovou hodnotou z funkce.</span><span class="sxs-lookup"><span data-stu-id="e2990-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2990-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2990-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2990-110">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="e2990-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2990-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2990-111">Requirements</span></span>  
 <span data-ttu-id="e2990-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2990-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2990-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e2990-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2990-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2990-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2990-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2990-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2990-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2990-116">See Also</span></span>  
    
    
    
 [<span data-ttu-id="e2990-117">Icordebugilframe3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2990-117">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 [<span data-ttu-id="e2990-118">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2990-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
