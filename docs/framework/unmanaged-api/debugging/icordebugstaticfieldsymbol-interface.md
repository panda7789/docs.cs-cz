---
title: ICorDebugStaticFieldSymbol – rozhraní
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 382f3fc9377c25379809badac0bc580c3593cbde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782587"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="e2bb1-102">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2bb1-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="e2bb1-103">Představuje informací symbolů ladění pro statické pole.</span><span class="sxs-lookup"><span data-stu-id="e2bb1-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e2bb1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e2bb1-104">Methods</span></span>  
  
|<span data-ttu-id="e2bb1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e2bb1-105">Method</span></span>|<span data-ttu-id="e2bb1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e2bb1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e2bb1-107">GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="e2bb1-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="e2bb1-108">Získá adresu statické pole.</span><span class="sxs-lookup"><span data-stu-id="e2bb1-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="e2bb1-109">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="e2bb1-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="e2bb1-110">Získá název statického pole.</span><span class="sxs-lookup"><span data-stu-id="e2bb1-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="e2bb1-111">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="e2bb1-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="e2bb1-112">Získá velikost v bajtech statické pole.</span><span class="sxs-lookup"><span data-stu-id="e2bb1-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2bb1-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2bb1-113">Remarks</span></span>  
 <span data-ttu-id="e2bb1-114">`ICorDebugStaticFieldSymbol` Rozhraní se používá k načtení informací symbolů ladění pro statické pole.</span><span class="sxs-lookup"><span data-stu-id="e2bb1-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2bb1-115">Toto rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e2bb1-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="e2bb1-116">Pokud se rozhodnete implementovat toto rozhraní ICorDebug scénářích mimo .NET Native, modul common language runtime bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e2bb1-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2bb1-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2bb1-117">Requirements</span></span>  
 <span data-ttu-id="e2bb1-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2bb1-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2bb1-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e2bb1-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2bb1-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2bb1-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2bb1-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2bb1-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2bb1-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2bb1-122">See also</span></span>

- [<span data-ttu-id="e2bb1-123">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2bb1-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="e2bb1-124">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e2bb1-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e2bb1-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="e2bb1-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
