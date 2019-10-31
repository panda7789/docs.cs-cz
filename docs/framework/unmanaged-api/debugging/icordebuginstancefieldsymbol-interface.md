---
title: ICorDebugInstanceFieldSymbol – rozhraní
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: 2ed1d70f554ca0a4a49639fe53a2ddbb0497c0a1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122724"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="25413-102">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25413-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="25413-103">Představuje informace o symbolech ladění pro pole instance.</span><span class="sxs-lookup"><span data-stu-id="25413-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="25413-104">Metody</span><span class="sxs-lookup"><span data-stu-id="25413-104">Methods</span></span>  
  
|<span data-ttu-id="25413-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="25413-105">Method</span></span>|<span data-ttu-id="25413-106">Popis</span><span class="sxs-lookup"><span data-stu-id="25413-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="25413-107">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="25413-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="25413-108">Získá název pole instance.</span><span class="sxs-lookup"><span data-stu-id="25413-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="25413-109">GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="25413-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="25413-110">Získá posun v bajtech tohoto pole instance v nadřazené třídě.</span><span class="sxs-lookup"><span data-stu-id="25413-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="25413-111">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="25413-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="25413-112">Získá velikost pole instance v bajtech.</span><span class="sxs-lookup"><span data-stu-id="25413-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25413-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25413-113">Remarks</span></span>  
 <span data-ttu-id="25413-114">Rozhraní `ICorDebugInstanceFieldSymbol` slouží k načtení informací o symbolu ladění pro pole instance.</span><span class="sxs-lookup"><span data-stu-id="25413-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25413-115">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="25413-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="25413-116">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="25413-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25413-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25413-117">Requirements</span></span>  
 <span data-ttu-id="25413-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25413-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25413-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="25413-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25413-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="25413-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25413-121">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25413-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25413-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25413-122">See also</span></span>

- [<span data-ttu-id="25413-123">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25413-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="25413-124">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="25413-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="25413-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="25413-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
