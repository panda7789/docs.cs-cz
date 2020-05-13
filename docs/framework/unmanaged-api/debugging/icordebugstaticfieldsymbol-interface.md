---
title: ICorDebugStaticFieldSymbol – rozhraní
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: f9b82f0f98a668555a8096d7575c049c31cae93a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379443"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="af3ef-102">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="af3ef-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="af3ef-103">Představuje informace o symbolech ladění pro statické pole.</span><span class="sxs-lookup"><span data-stu-id="af3ef-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="af3ef-104">Metody</span><span class="sxs-lookup"><span data-stu-id="af3ef-104">Methods</span></span>  
  
|<span data-ttu-id="af3ef-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="af3ef-105">Method</span></span>|<span data-ttu-id="af3ef-106">Popis</span><span class="sxs-lookup"><span data-stu-id="af3ef-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="af3ef-107">GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="af3ef-107">GetAddress Method</span></span>](icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="af3ef-108">Získá adresu statického pole.</span><span class="sxs-lookup"><span data-stu-id="af3ef-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="af3ef-109">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="af3ef-109">GetName Method</span></span>](icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="af3ef-110">Získá název statického pole.</span><span class="sxs-lookup"><span data-stu-id="af3ef-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="af3ef-111">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="af3ef-111">GetSize Method</span></span>](icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="af3ef-112">Získá velikost statického pole v bajtech.</span><span class="sxs-lookup"><span data-stu-id="af3ef-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af3ef-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="af3ef-113">Remarks</span></span>  
 <span data-ttu-id="af3ef-114">`ICorDebugStaticFieldSymbol`Rozhraní se používá k načtení informací o ladicím symbolu pro statické pole.</span><span class="sxs-lookup"><span data-stu-id="af3ef-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af3ef-115">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="af3ef-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="af3ef-116">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="af3ef-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af3ef-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="af3ef-117">Requirements</span></span>  
 <span data-ttu-id="af3ef-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af3ef-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af3ef-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="af3ef-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af3ef-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="af3ef-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af3ef-121">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af3ef-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af3ef-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="af3ef-122">See also</span></span>

- [<span data-ttu-id="af3ef-123">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="af3ef-123">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="af3ef-124">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="af3ef-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="af3ef-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="af3ef-125">Debugging</span></span>](index.md)
