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
ms.openlocfilehash: fbf3f07f5669c4fcafa4d3cc4119fc715539651d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="b0ee7-102">ICorDebugInstanceFieldSymbol rozhraní</span><span class="sxs-lookup"><span data-stu-id="b0ee7-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="b0ee7-103">Představuje informace o ladění symbol pro pole instance.</span><span class="sxs-lookup"><span data-stu-id="b0ee7-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b0ee7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b0ee7-104">Methods</span></span>  
  
|<span data-ttu-id="b0ee7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b0ee7-105">Method</span></span>|<span data-ttu-id="b0ee7-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b0ee7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b0ee7-107">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="b0ee7-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="b0ee7-108">Získá název pole instance.</span><span class="sxs-lookup"><span data-stu-id="b0ee7-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="b0ee7-109">Getoffset – metoda</span><span class="sxs-lookup"><span data-stu-id="b0ee7-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="b0ee7-110">Získá posun v bajtech tohoto pole instance ve své nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="b0ee7-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="b0ee7-111">Getsize – metoda</span><span class="sxs-lookup"><span data-stu-id="b0ee7-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="b0ee7-112">Získá velikost v bajtech pole instance.</span><span class="sxs-lookup"><span data-stu-id="b0ee7-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0ee7-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b0ee7-113">Remarks</span></span>  
 <span data-ttu-id="b0ee7-114">`ICorDebugInstanceFieldSymbol` Rozhraní se používá k načtení informací o symbolu ladění pro pole instance.</span><span class="sxs-lookup"><span data-stu-id="b0ee7-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0ee7-115">Toto rozhraní je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="b0ee7-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="b0ee7-116">Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b0ee7-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0ee7-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0ee7-117">Requirements</span></span>  
 <span data-ttu-id="b0ee7-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0ee7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0ee7-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0ee7-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0ee7-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0ee7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0ee7-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0ee7-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0ee7-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0ee7-122">See Also</span></span>  
 [<span data-ttu-id="b0ee7-123">ICorDebugStaticFieldSymbol rozhraní</span><span class="sxs-lookup"><span data-stu-id="b0ee7-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="b0ee7-124">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="b0ee7-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b0ee7-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="b0ee7-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
