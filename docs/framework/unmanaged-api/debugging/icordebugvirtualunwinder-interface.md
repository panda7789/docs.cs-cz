---
title: Rozhraní ICorDebugVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb04ac42b3cc77db3af53c87efb0d1f1f75da928
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421282"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="a36c9-102">Rozhraní ICorDebugVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="a36c9-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="a36c9-103">Poskytuje metody, které pomohou v uvolnění zásobníku.</span><span class="sxs-lookup"><span data-stu-id="a36c9-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a36c9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a36c9-104">Methods</span></span>  
  
|<span data-ttu-id="a36c9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a36c9-105">Method</span></span>|<span data-ttu-id="a36c9-106">Název</span><span class="sxs-lookup"><span data-stu-id="a36c9-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="a36c9-107">GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="a36c9-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="a36c9-108">Získá aktuální kontext tento unwinder.</span><span class="sxs-lookup"><span data-stu-id="a36c9-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="a36c9-109">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="a36c9-109">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="a36c9-110">Přejde k kontextu volajícího.</span><span class="sxs-lookup"><span data-stu-id="a36c9-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a36c9-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a36c9-111">Remarks</span></span>  
 <span data-ttu-id="a36c9-112">Členové `ICorDebugVirtualUnwinder` rozhraní je implementováno modulem ladicího programu při uvolnění zásobníku.</span><span class="sxs-lookup"><span data-stu-id="a36c9-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a36c9-113">Toto rozhraní je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="a36c9-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="a36c9-114">Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a36c9-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a36c9-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a36c9-115">Requirements</span></span>  
 <span data-ttu-id="a36c9-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a36c9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a36c9-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a36c9-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a36c9-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a36c9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a36c9-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a36c9-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a36c9-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="a36c9-120">See Also</span></span>  
 [<span data-ttu-id="a36c9-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a36c9-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a36c9-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="a36c9-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
