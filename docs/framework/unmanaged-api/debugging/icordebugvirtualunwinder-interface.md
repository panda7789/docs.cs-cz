---
title: Rozhraní ICorDebugVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9db6b83e2feedd761b95dec455213051e37366e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684142"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="ba69a-102">Rozhraní ICorDebugVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="ba69a-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="ba69a-103">Poskytuje metody, které vám pomůžou odvíjení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="ba69a-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ba69a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ba69a-104">Methods</span></span>  
  
|<span data-ttu-id="ba69a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ba69a-105">Method</span></span>|<span data-ttu-id="ba69a-106">Název</span><span class="sxs-lookup"><span data-stu-id="ba69a-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="ba69a-107">GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="ba69a-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="ba69a-108">Získá aktuální kontext tohoto unwinder.</span><span class="sxs-lookup"><span data-stu-id="ba69a-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="ba69a-109">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="ba69a-109">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="ba69a-110">Přejde k kontextu volajícího.</span><span class="sxs-lookup"><span data-stu-id="ba69a-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba69a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ba69a-111">Remarks</span></span>  
 <span data-ttu-id="ba69a-112">Členové `ICorDebugVirtualUnwinder` rozhraní jsou implementovány pomocí ladicího programu, které vám pomůžou odvíjení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="ba69a-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba69a-113">Toto rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ba69a-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="ba69a-114">Pokud se rozhodnete implementovat toto rozhraní ICorDebug scénářích mimo .NET Native, modul common language runtime bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ba69a-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba69a-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ba69a-115">Requirements</span></span>  
 <span data-ttu-id="ba69a-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba69a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba69a-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba69a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba69a-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba69a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba69a-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba69a-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba69a-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba69a-120">See also</span></span>
- [<span data-ttu-id="ba69a-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ba69a-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ba69a-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="ba69a-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
