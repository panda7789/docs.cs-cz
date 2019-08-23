---
title: ICorDebugStaticFieldSymbol – rozhraní
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f4e245e96ac9d47db10072e50a5b3c516d5dd27
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962682"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="00ef6-102">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00ef6-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="00ef6-103">Představuje informace o symbolech ladění pro statické pole.</span><span class="sxs-lookup"><span data-stu-id="00ef6-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="00ef6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="00ef6-104">Methods</span></span>  
  
|<span data-ttu-id="00ef6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="00ef6-105">Method</span></span>|<span data-ttu-id="00ef6-106">Popis</span><span class="sxs-lookup"><span data-stu-id="00ef6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="00ef6-107">GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="00ef6-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="00ef6-108">Získá adresu statického pole.</span><span class="sxs-lookup"><span data-stu-id="00ef6-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="00ef6-109">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="00ef6-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="00ef6-110">Získá název statického pole.</span><span class="sxs-lookup"><span data-stu-id="00ef6-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="00ef6-111">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="00ef6-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="00ef6-112">Získá velikost statického pole v bajtech.</span><span class="sxs-lookup"><span data-stu-id="00ef6-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00ef6-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00ef6-113">Remarks</span></span>  
 <span data-ttu-id="00ef6-114">`ICorDebugStaticFieldSymbol` Rozhraní se používá k načtení informací o ladicím symbolu pro statické pole.</span><span class="sxs-lookup"><span data-stu-id="00ef6-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00ef6-115">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="00ef6-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="00ef6-116">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="00ef6-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00ef6-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00ef6-117">Requirements</span></span>  
 <span data-ttu-id="00ef6-118">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00ef6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00ef6-119">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="00ef6-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00ef6-120">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00ef6-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00ef6-121">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00ef6-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00ef6-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00ef6-122">See also</span></span>

- [<span data-ttu-id="00ef6-123">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00ef6-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="00ef6-124">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="00ef6-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="00ef6-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="00ef6-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
