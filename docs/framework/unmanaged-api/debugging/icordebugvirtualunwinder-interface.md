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
ms.workload: dotnet
ms.openlocfilehash: 936df5c3d913a2ee5a1648906fb3ece2751d8ef5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="7b361-102">Rozhraní ICorDebugVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="7b361-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="7b361-103">Poskytuje metody, které pomohou v uvolnění zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7b361-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7b361-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7b361-104">Methods</span></span>  
  
|<span data-ttu-id="7b361-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7b361-105">Method</span></span>|<span data-ttu-id="7b361-106">Název</span><span class="sxs-lookup"><span data-stu-id="7b361-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="7b361-107">GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="7b361-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="7b361-108">Získá aktuální kontext tento unwinder.</span><span class="sxs-lookup"><span data-stu-id="7b361-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="7b361-109">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="7b361-109">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="7b361-110">Přejde k kontextu volajícího.</span><span class="sxs-lookup"><span data-stu-id="7b361-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b361-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b361-111">Remarks</span></span>  
 <span data-ttu-id="7b361-112">Členové `ICorDebugVirtualUnwinder` rozhraní je implementováno modulem ladicího programu při uvolnění zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7b361-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b361-113">Toto rozhraní je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="7b361-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="7b361-114">Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7b361-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b361-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b361-115">Requirements</span></span>  
 <span data-ttu-id="7b361-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b361-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b361-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b361-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b361-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b361-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b361-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b361-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b361-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b361-120">See Also</span></span>  
 [<span data-ttu-id="7b361-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7b361-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="7b361-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="7b361-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
