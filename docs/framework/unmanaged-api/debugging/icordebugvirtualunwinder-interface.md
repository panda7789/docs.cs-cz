---
title: Rozhraní ICorDebugVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f78417d613023bb4fb7325560c0c06abe0874aba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967944"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="9813b-102">Rozhraní ICorDebugVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="9813b-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="9813b-103">Poskytuje metody, které vám pomůžou při odvíjení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="9813b-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9813b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9813b-104">Methods</span></span>  
  
|<span data-ttu-id="9813b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9813b-105">Method</span></span>|<span data-ttu-id="9813b-106">Name</span><span class="sxs-lookup"><span data-stu-id="9813b-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="9813b-107">GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="9813b-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="9813b-108">Získá aktuální kontext tohoto unwind.</span><span class="sxs-lookup"><span data-stu-id="9813b-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="9813b-109">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="9813b-109">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="9813b-110">Přejde do kontextu volajícího.</span><span class="sxs-lookup"><span data-stu-id="9813b-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9813b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9813b-111">Remarks</span></span>  
 <span data-ttu-id="9813b-112">Členové `ICorDebugVirtualUnwinder` rozhraní jsou implementováni pomocí ladicího programu, aby mohli pomáhat při uvolňování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="9813b-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9813b-113">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9813b-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="9813b-114">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="9813b-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9813b-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9813b-115">Requirements</span></span>  
 <span data-ttu-id="9813b-116">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9813b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9813b-117">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9813b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9813b-118">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9813b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9813b-119">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9813b-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9813b-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9813b-120">See also</span></span>

- [<span data-ttu-id="9813b-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9813b-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="9813b-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="9813b-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
