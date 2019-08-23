---
title: ICorDebugVariableSymbol – rozhraní
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3fb2538894184c19bc107ce52cbef3ac86a97345
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967980"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="95311-102">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95311-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="95311-103">Načte informace o ladicím symbolu pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="95311-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="95311-104">Metody</span><span class="sxs-lookup"><span data-stu-id="95311-104">Methods</span></span>  
  
|<span data-ttu-id="95311-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="95311-105">Method</span></span>|<span data-ttu-id="95311-106">Popis</span><span class="sxs-lookup"><span data-stu-id="95311-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="95311-107">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="95311-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="95311-108">Získá název proměnné.</span><span class="sxs-lookup"><span data-stu-id="95311-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="95311-109">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="95311-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="95311-110">Získá velikost proměnné v bajtech.</span><span class="sxs-lookup"><span data-stu-id="95311-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="95311-111">GetSlotIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="95311-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="95311-112">Načte index spravovaného slotu místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="95311-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="95311-113">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="95311-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="95311-114">Získá hodnotu proměnné jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="95311-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="95311-115">SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="95311-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="95311-116">Přiřadí hodnotu bajtového pole proměnné.</span><span class="sxs-lookup"><span data-stu-id="95311-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95311-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="95311-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95311-118">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="95311-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="95311-119">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="95311-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95311-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="95311-120">Requirements</span></span>  
 <span data-ttu-id="95311-121">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95311-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95311-122">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="95311-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95311-123">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95311-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95311-124">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95311-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95311-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95311-125">See also</span></span>

- [<span data-ttu-id="95311-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="95311-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="95311-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="95311-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
