---
title: "ICorDebugCode4 rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name:
- ICorDebugCode4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4
helpviewer_keywords:
- ICorDebugCode4 interface [.NET Framework debugging]
ms.assetid: a3fdf523-274a-449c-920b-9fcb0aed1d97
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 30c0599e183d51030ac5b063a2aca4352ad95eca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="63888-102">ICorDebugCode4 rozhraní</span><span class="sxs-lookup"><span data-stu-id="63888-102">ICorDebugCode4 Interface</span></span>
<span data-ttu-id="63888-103">Poskytne metodu, která umožňuje ladicí program výčet místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="63888-103">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63888-104">Metody</span><span class="sxs-lookup"><span data-stu-id="63888-104">Methods</span></span>  
  
|<span data-ttu-id="63888-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="63888-105">Method</span></span>|<span data-ttu-id="63888-106">Popis</span><span class="sxs-lookup"><span data-stu-id="63888-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63888-107">EnumerateVariableHomes – metoda</span><span class="sxs-lookup"><span data-stu-id="63888-107">EnumerateVariableHomes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="63888-108">Získá enumerátor pro místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="63888-108">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63888-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="63888-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63888-110">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="63888-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63888-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63888-111">Requirements</span></span>  
 <span data-ttu-id="63888-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63888-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63888-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63888-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63888-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63888-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63888-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63888-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63888-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="63888-116">See Also</span></span>  
    
    
 [<span data-ttu-id="63888-117">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63888-117">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="63888-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="63888-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
