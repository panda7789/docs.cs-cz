---
title: "ICorDebugStaticFieldSymbol rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a25e19bf43d852670bc5f4f491fb25707395e04a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="8def4-102">ICorDebugStaticFieldSymbol rozhraní</span><span class="sxs-lookup"><span data-stu-id="8def4-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="8def4-103">Představuje informace o ladění symbol pro statické pole.</span><span class="sxs-lookup"><span data-stu-id="8def4-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8def4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8def4-104">Methods</span></span>  
  
|<span data-ttu-id="8def4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8def4-105">Method</span></span>|<span data-ttu-id="8def4-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8def4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8def4-107">GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="8def4-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="8def4-108">Získá adresu statického pole.</span><span class="sxs-lookup"><span data-stu-id="8def4-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="8def4-109">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="8def4-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="8def4-110">Získá název statického pole.</span><span class="sxs-lookup"><span data-stu-id="8def4-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="8def4-111">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="8def4-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="8def4-112">Získá velikost v bajtech statického pole.</span><span class="sxs-lookup"><span data-stu-id="8def4-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8def4-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8def4-113">Remarks</span></span>  
 <span data-ttu-id="8def4-114">`ICorDebugStaticFieldSymbol` Rozhraní se používá k načtení informací o symbolu ladění pro statické pole.</span><span class="sxs-lookup"><span data-stu-id="8def4-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8def4-115">Toto rozhraní je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="8def4-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="8def4-116">Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8def4-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8def4-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8def4-117">Requirements</span></span>  
 <span data-ttu-id="8def4-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8def4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8def4-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8def4-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8def4-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8def4-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8def4-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8def4-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8def4-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="8def4-122">See Also</span></span>  
 [<span data-ttu-id="8def4-123">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8def4-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="8def4-124">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8def4-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8def4-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="8def4-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
