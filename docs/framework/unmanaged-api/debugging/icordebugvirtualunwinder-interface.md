---
title: Rozhraní ICorDebugVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: 065f71e45c2a56dbaa16a45f70958ca3dea80c48
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790828"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="0beda-102">Rozhraní ICorDebugVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="0beda-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="0beda-103">Poskytuje metody, které vám pomůžou při odvíjení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0beda-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0beda-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0beda-104">Methods</span></span>  
  
|<span data-ttu-id="0beda-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0beda-105">Method</span></span>|<span data-ttu-id="0beda-106">Name</span><span class="sxs-lookup"><span data-stu-id="0beda-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="0beda-107">GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="0beda-107">GetContext Method</span></span>](icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="0beda-108">Získá aktuální kontext tohoto unwind.</span><span class="sxs-lookup"><span data-stu-id="0beda-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="0beda-109">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="0beda-109">Next Method</span></span>](icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="0beda-110">Přejde do kontextu volajícího.</span><span class="sxs-lookup"><span data-stu-id="0beda-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0beda-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0beda-111">Remarks</span></span>  
 <span data-ttu-id="0beda-112">Členy rozhraní `ICorDebugVirtualUnwinder` jsou implementovány pomocí ladicího programu, aby bylo možné v zásobníku převinout zpět.</span><span class="sxs-lookup"><span data-stu-id="0beda-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0beda-113">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0beda-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="0beda-114">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="0beda-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0beda-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0beda-115">Requirements</span></span>  
 <span data-ttu-id="0beda-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0beda-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0beda-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0beda-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0beda-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0beda-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0beda-119">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0beda-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0beda-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0beda-120">See also</span></span>

- [<span data-ttu-id="0beda-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0beda-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0beda-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="0beda-122">Debugging</span></span>](index.md)
