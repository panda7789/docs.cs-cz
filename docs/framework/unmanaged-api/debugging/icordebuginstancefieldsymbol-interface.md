---
title: "ICorDebugInstanceFieldSymbol rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b13df0d70a36e475e87bae3152912e58a9f8443
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="b3ba2-102">ICorDebugInstanceFieldSymbol rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3ba2-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="b3ba2-103">Představuje informace o ladění symbol pro pole instance.</span><span class="sxs-lookup"><span data-stu-id="b3ba2-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b3ba2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b3ba2-104">Methods</span></span>  
  
|<span data-ttu-id="b3ba2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b3ba2-105">Method</span></span>|<span data-ttu-id="b3ba2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b3ba2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b3ba2-107">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="b3ba2-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="b3ba2-108">Získá název pole instance.</span><span class="sxs-lookup"><span data-stu-id="b3ba2-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="b3ba2-109">GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="b3ba2-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="b3ba2-110">Získá posun v bajtech tohoto pole instance ve své nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="b3ba2-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="b3ba2-111">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="b3ba2-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="b3ba2-112">Získá velikost v bajtech pole instance.</span><span class="sxs-lookup"><span data-stu-id="b3ba2-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3ba2-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3ba2-113">Remarks</span></span>  
 <span data-ttu-id="b3ba2-114">`ICorDebugInstanceFieldSymbol` Rozhraní se používá k načtení informací o symbolu ladění pro pole instance.</span><span class="sxs-lookup"><span data-stu-id="b3ba2-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3ba2-115">Toto rozhraní je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="b3ba2-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="b3ba2-116">Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b3ba2-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3ba2-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b3ba2-117">Requirements</span></span>  
 <span data-ttu-id="b3ba2-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3ba2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3ba2-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3ba2-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3ba2-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3ba2-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3ba2-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3ba2-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3ba2-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3ba2-122">See Also</span></span>  
 [<span data-ttu-id="b3ba2-123">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3ba2-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="b3ba2-124">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b3ba2-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b3ba2-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="b3ba2-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
