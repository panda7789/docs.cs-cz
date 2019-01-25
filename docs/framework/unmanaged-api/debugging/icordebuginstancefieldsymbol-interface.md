---
title: ICorDebugInstanceFieldSymbol Interface
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 082d8e8c8b57b7d0938f59aebbe08e35a7e3f7df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560730"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="eb62d-102">ICorDebugInstanceFieldSymbol Interface</span><span class="sxs-lookup"><span data-stu-id="eb62d-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="eb62d-103">Představuje informací symbolů ladění pro pole instance.</span><span class="sxs-lookup"><span data-stu-id="eb62d-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eb62d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="eb62d-104">Methods</span></span>  
  
|<span data-ttu-id="eb62d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="eb62d-105">Method</span></span>|<span data-ttu-id="eb62d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="eb62d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eb62d-107">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="eb62d-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="eb62d-108">Získá název pole instance.</span><span class="sxs-lookup"><span data-stu-id="eb62d-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="eb62d-109">GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="eb62d-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="eb62d-110">Získá posun v bajtech tohoto pole instance v její nadřazené třídě.</span><span class="sxs-lookup"><span data-stu-id="eb62d-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="eb62d-111">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="eb62d-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="eb62d-112">Získá velikost v bajtech pole instance.</span><span class="sxs-lookup"><span data-stu-id="eb62d-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb62d-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb62d-113">Remarks</span></span>  
 <span data-ttu-id="eb62d-114">`ICorDebugInstanceFieldSymbol` Rozhraní se používá k načtení informací symbolů ladění pro pole instance.</span><span class="sxs-lookup"><span data-stu-id="eb62d-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb62d-115">Toto rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="eb62d-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="eb62d-116">Pokud se rozhodnete implementovat toto rozhraní ICorDebug scénářích mimo .NET Native, modul common language runtime bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="eb62d-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb62d-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eb62d-117">Requirements</span></span>  
 <span data-ttu-id="eb62d-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb62d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb62d-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb62d-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb62d-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb62d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb62d-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb62d-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb62d-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb62d-122">See also</span></span>
- [<span data-ttu-id="eb62d-123">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb62d-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="eb62d-124">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="eb62d-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="eb62d-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="eb62d-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
