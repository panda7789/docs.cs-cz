---
title: ICorDebugVariableSymbol – rozhraní
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
ms.openlocfilehash: 25ffa55eeeb82d6feaf5696ea96dae81774e3d70
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121917"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="b57e1-102">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b57e1-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="b57e1-103">Načte informace o ladicím symbolu pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="b57e1-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b57e1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b57e1-104">Methods</span></span>  
  
|<span data-ttu-id="b57e1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b57e1-105">Method</span></span>|<span data-ttu-id="b57e1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b57e1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b57e1-107">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="b57e1-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="b57e1-108">Získá název proměnné.</span><span class="sxs-lookup"><span data-stu-id="b57e1-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="b57e1-109">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="b57e1-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="b57e1-110">Získá velikost proměnné v bajtech.</span><span class="sxs-lookup"><span data-stu-id="b57e1-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="b57e1-111">GetSlotIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="b57e1-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="b57e1-112">Načte index spravovaného slotu místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="b57e1-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="b57e1-113">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="b57e1-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="b57e1-114">Získá hodnotu proměnné jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="b57e1-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="b57e1-115">SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="b57e1-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="b57e1-116">Přiřadí hodnotu bajtového pole proměnné.</span><span class="sxs-lookup"><span data-stu-id="b57e1-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b57e1-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b57e1-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b57e1-118">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b57e1-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="b57e1-119">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="b57e1-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b57e1-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b57e1-120">Requirements</span></span>  
 <span data-ttu-id="b57e1-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b57e1-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b57e1-122">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b57e1-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b57e1-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b57e1-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b57e1-124">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b57e1-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b57e1-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b57e1-125">See also</span></span>

- [<span data-ttu-id="b57e1-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b57e1-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b57e1-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="b57e1-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
