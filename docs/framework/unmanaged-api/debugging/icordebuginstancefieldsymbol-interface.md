---
title: ICorDebugInstanceFieldSymbol – rozhraní
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: 092f2a8acdffa9f91176bdf0ca10b8db9cff6d37
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209926"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="68e43-102">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68e43-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="68e43-103">Představuje informace o symbolech ladění pro pole instance.</span><span class="sxs-lookup"><span data-stu-id="68e43-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="68e43-104">Metody</span><span class="sxs-lookup"><span data-stu-id="68e43-104">Methods</span></span>  
  
|<span data-ttu-id="68e43-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="68e43-105">Method</span></span>|<span data-ttu-id="68e43-106">Popis</span><span class="sxs-lookup"><span data-stu-id="68e43-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="68e43-107">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="68e43-107">GetName Method</span></span>](icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="68e43-108">Získá název pole instance.</span><span class="sxs-lookup"><span data-stu-id="68e43-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="68e43-109">GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="68e43-109">GetOffset Method</span></span>](icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="68e43-110">Získá posun v bajtech tohoto pole instance v nadřazené třídě.</span><span class="sxs-lookup"><span data-stu-id="68e43-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="68e43-111">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="68e43-111">GetSize Method</span></span>](icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="68e43-112">Získá velikost pole instance v bajtech.</span><span class="sxs-lookup"><span data-stu-id="68e43-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68e43-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="68e43-113">Remarks</span></span>  
 <span data-ttu-id="68e43-114">`ICorDebugInstanceFieldSymbol`Rozhraní se používá k načtení informací o ladicím symbolu pro pole instance.</span><span class="sxs-lookup"><span data-stu-id="68e43-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="68e43-115">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="68e43-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="68e43-116">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="68e43-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68e43-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="68e43-117">Requirements</span></span>  
 <span data-ttu-id="68e43-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68e43-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68e43-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="68e43-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68e43-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="68e43-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68e43-121">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68e43-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68e43-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="68e43-122">See also</span></span>

- [<span data-ttu-id="68e43-123">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68e43-123">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="68e43-124">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68e43-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="68e43-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="68e43-125">Debugging</span></span>](index.md)
