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
ms.openlocfilehash: b747d2d43fd7ff4dc901dff14277dbce9606497f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="e4e75-102">ICorDebugStaticFieldSymbol rozhraní</span><span class="sxs-lookup"><span data-stu-id="e4e75-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="e4e75-103">Představuje informace o ladění symbol pro statické pole.</span><span class="sxs-lookup"><span data-stu-id="e4e75-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e4e75-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e4e75-104">Methods</span></span>  
  
|<span data-ttu-id="e4e75-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e4e75-105">Method</span></span>|<span data-ttu-id="e4e75-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e4e75-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e4e75-107">Getaddress – metoda</span><span class="sxs-lookup"><span data-stu-id="e4e75-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="e4e75-108">Získá adresu statického pole.</span><span class="sxs-lookup"><span data-stu-id="e4e75-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="e4e75-109">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="e4e75-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="e4e75-110">Získá název statického pole.</span><span class="sxs-lookup"><span data-stu-id="e4e75-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="e4e75-111">Getsize – metoda</span><span class="sxs-lookup"><span data-stu-id="e4e75-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="e4e75-112">Získá velikost v bajtech statického pole.</span><span class="sxs-lookup"><span data-stu-id="e4e75-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4e75-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e4e75-113">Remarks</span></span>  
 <span data-ttu-id="e4e75-114">`ICorDebugStaticFieldSymbol` Rozhraní se používá k načtení informací o symbolu ladění pro statické pole.</span><span class="sxs-lookup"><span data-stu-id="e4e75-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4e75-115">Toto rozhraní je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="e4e75-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="e4e75-116">Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e4e75-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4e75-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e4e75-117">Requirements</span></span>  
 <span data-ttu-id="e4e75-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4e75-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4e75-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4e75-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4e75-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4e75-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4e75-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4e75-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4e75-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4e75-122">See Also</span></span>  
 [<span data-ttu-id="e4e75-123">ICorDebugInstanceFieldSymbol rozhraní</span><span class="sxs-lookup"><span data-stu-id="e4e75-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="e4e75-124">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="e4e75-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="e4e75-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="e4e75-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
