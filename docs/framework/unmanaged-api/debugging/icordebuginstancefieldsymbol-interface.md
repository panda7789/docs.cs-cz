---
title: ICorDebugInstanceFieldSymbol – rozhraní
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: 41258b0eeed5fbf8ab86546f74073f8eeaa3085c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777517"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="e1704-102">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e1704-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="e1704-103">Představuje informace o symbolech ladění pro pole instance.</span><span class="sxs-lookup"><span data-stu-id="e1704-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e1704-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e1704-104">Methods</span></span>  
  
|<span data-ttu-id="e1704-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e1704-105">Method</span></span>|<span data-ttu-id="e1704-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e1704-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e1704-107">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="e1704-107">GetName Method</span></span>](icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="e1704-108">Získá název pole instance.</span><span class="sxs-lookup"><span data-stu-id="e1704-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="e1704-109">GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="e1704-109">GetOffset Method</span></span>](icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="e1704-110">Získá posun v bajtech tohoto pole instance v nadřazené třídě.</span><span class="sxs-lookup"><span data-stu-id="e1704-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="e1704-111">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="e1704-111">GetSize Method</span></span>](icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="e1704-112">Získá velikost pole instance v bajtech.</span><span class="sxs-lookup"><span data-stu-id="e1704-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1704-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e1704-113">Remarks</span></span>  
 <span data-ttu-id="e1704-114">Rozhraní `ICorDebugInstanceFieldSymbol` slouží k načtení informací o symbolu ladění pro pole instance.</span><span class="sxs-lookup"><span data-stu-id="e1704-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1704-115">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e1704-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="e1704-116">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="e1704-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1704-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e1704-117">Requirements</span></span>  
 <span data-ttu-id="e1704-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1704-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1704-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e1704-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1704-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e1704-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1704-121">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1704-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1704-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1704-122">See also</span></span>

- [<span data-ttu-id="e1704-123">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e1704-123">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="e1704-124">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e1704-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e1704-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="e1704-125">Debugging</span></span>](index.md)
