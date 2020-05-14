---
title: Rozhraní ICorDebugVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: 59ecf3da4b44af7b04dec26fbc3ea182c185d04a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396456"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="43be7-102">Rozhraní ICorDebugVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="43be7-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="43be7-103">Poskytuje metody, které vám pomůžou při odvíjení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="43be7-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="43be7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="43be7-104">Methods</span></span>  
  
|<span data-ttu-id="43be7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="43be7-105">Method</span></span>|<span data-ttu-id="43be7-106">Name</span><span class="sxs-lookup"><span data-stu-id="43be7-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="43be7-107">GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="43be7-107">GetContext Method</span></span>](icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="43be7-108">Získá aktuální kontext tohoto unwind.</span><span class="sxs-lookup"><span data-stu-id="43be7-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="43be7-109">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="43be7-109">Next Method</span></span>](icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="43be7-110">Přejde do kontextu volajícího.</span><span class="sxs-lookup"><span data-stu-id="43be7-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43be7-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43be7-111">Remarks</span></span>  
 <span data-ttu-id="43be7-112">Členové `ICorDebugVirtualUnwinder` rozhraní jsou implementováni pomocí ladicího programu, aby mohli pomáhat při uvolňování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="43be7-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="43be7-113">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="43be7-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="43be7-114">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="43be7-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43be7-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="43be7-115">Requirements</span></span>  
 <span data-ttu-id="43be7-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43be7-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43be7-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="43be7-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43be7-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="43be7-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43be7-119">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43be7-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43be7-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="43be7-120">See also</span></span>

- [<span data-ttu-id="43be7-121">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="43be7-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="43be7-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="43be7-122">Debugging</span></span>](index.md)
