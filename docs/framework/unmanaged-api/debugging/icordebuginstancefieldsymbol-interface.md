---
title: ICorDebugInstanceFieldSymbol – rozhraní
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e5f63df9354df6a4d142c2f6ae12f9a0d5600fb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910142"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="643ca-102">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="643ca-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="643ca-103">Představuje informace o symbolech ladění pro pole instance.</span><span class="sxs-lookup"><span data-stu-id="643ca-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="643ca-104">Metody</span><span class="sxs-lookup"><span data-stu-id="643ca-104">Methods</span></span>  
  
|<span data-ttu-id="643ca-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="643ca-105">Method</span></span>|<span data-ttu-id="643ca-106">Popis</span><span class="sxs-lookup"><span data-stu-id="643ca-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="643ca-107">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="643ca-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="643ca-108">Získá název pole instance.</span><span class="sxs-lookup"><span data-stu-id="643ca-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="643ca-109">GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="643ca-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="643ca-110">Získá posun v bajtech tohoto pole instance v nadřazené třídě.</span><span class="sxs-lookup"><span data-stu-id="643ca-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="643ca-111">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="643ca-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="643ca-112">Získá velikost pole instance v bajtech.</span><span class="sxs-lookup"><span data-stu-id="643ca-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="643ca-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="643ca-113">Remarks</span></span>  
 <span data-ttu-id="643ca-114">`ICorDebugInstanceFieldSymbol` Rozhraní se používá k načtení informací o ladicím symbolu pro pole instance.</span><span class="sxs-lookup"><span data-stu-id="643ca-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="643ca-115">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="643ca-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="643ca-116">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="643ca-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="643ca-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="643ca-117">Requirements</span></span>  
 <span data-ttu-id="643ca-118">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="643ca-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="643ca-119">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="643ca-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="643ca-120">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="643ca-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="643ca-121">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="643ca-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="643ca-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="643ca-122">See also</span></span>

- [<span data-ttu-id="643ca-123">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="643ca-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="643ca-124">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="643ca-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="643ca-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="643ca-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
