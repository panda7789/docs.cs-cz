---
title: "Rozhraní ICorDebugVirtualUnwinder"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d22fa926b300384b7f790468b1b3d0becafdb942
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="8e482-102">Rozhraní ICorDebugVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="8e482-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="8e482-103">Poskytuje metody, které pomohou v uvolnění zásobníku.</span><span class="sxs-lookup"><span data-stu-id="8e482-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8e482-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8e482-104">Methods</span></span>  
  
|<span data-ttu-id="8e482-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8e482-105">Method</span></span>|<span data-ttu-id="8e482-106">Název</span><span class="sxs-lookup"><span data-stu-id="8e482-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="8e482-107">Getcontext – metoda</span><span class="sxs-lookup"><span data-stu-id="8e482-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="8e482-108">Získá aktuální kontext tento unwinder.</span><span class="sxs-lookup"><span data-stu-id="8e482-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="8e482-109">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="8e482-109">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="8e482-110">Přejde k kontextu volajícího.</span><span class="sxs-lookup"><span data-stu-id="8e482-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e482-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8e482-111">Remarks</span></span>  
 <span data-ttu-id="8e482-112">Členové `ICorDebugVirtualUnwinder` rozhraní je implementováno modulem ladicího programu při uvolnění zásobníku.</span><span class="sxs-lookup"><span data-stu-id="8e482-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e482-113">Toto rozhraní je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="8e482-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="8e482-114">Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8e482-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e482-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8e482-115">Requirements</span></span>  
 <span data-ttu-id="8e482-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e482-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e482-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8e482-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e482-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e482-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e482-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e482-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e482-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e482-120">See Also</span></span>  
 [<span data-ttu-id="8e482-121">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="8e482-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8e482-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="8e482-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
