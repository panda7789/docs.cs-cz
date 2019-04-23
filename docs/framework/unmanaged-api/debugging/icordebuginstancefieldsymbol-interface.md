---
title: ICorDebugInstanceFieldSymbol – rozhraní
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5c0759989e069169c7e68b71206d9a50b04ad63
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111485"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="bdd0a-102">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bdd0a-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="bdd0a-103">Představuje informací symbolů ladění pro pole instance.</span><span class="sxs-lookup"><span data-stu-id="bdd0a-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bdd0a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bdd0a-104">Methods</span></span>  
  
|<span data-ttu-id="bdd0a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bdd0a-105">Method</span></span>|<span data-ttu-id="bdd0a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="bdd0a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bdd0a-107">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="bdd0a-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="bdd0a-108">Získá název pole instance.</span><span class="sxs-lookup"><span data-stu-id="bdd0a-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="bdd0a-109">GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="bdd0a-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="bdd0a-110">Získá posun v bajtech tohoto pole instance v její nadřazené třídě.</span><span class="sxs-lookup"><span data-stu-id="bdd0a-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="bdd0a-111">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="bdd0a-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="bdd0a-112">Získá velikost v bajtech pole instance.</span><span class="sxs-lookup"><span data-stu-id="bdd0a-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdd0a-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bdd0a-113">Remarks</span></span>  
 <span data-ttu-id="bdd0a-114">`ICorDebugInstanceFieldSymbol` Rozhraní se používá k načtení informací symbolů ladění pro pole instance.</span><span class="sxs-lookup"><span data-stu-id="bdd0a-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdd0a-115">Toto rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bdd0a-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="bdd0a-116">Pokud se rozhodnete implementovat toto rozhraní ICorDebug scénářích mimo .NET Native, modul common language runtime bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bdd0a-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdd0a-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bdd0a-117">Requirements</span></span>  
 <span data-ttu-id="bdd0a-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdd0a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdd0a-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bdd0a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdd0a-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdd0a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdd0a-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdd0a-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdd0a-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bdd0a-122">See also</span></span>

- [<span data-ttu-id="bdd0a-123">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bdd0a-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="bdd0a-124">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="bdd0a-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="bdd0a-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="bdd0a-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
