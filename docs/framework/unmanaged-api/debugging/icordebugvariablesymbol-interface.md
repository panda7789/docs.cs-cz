---
title: ICorDebugVariableSymbol – rozhraní
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
ms.openlocfilehash: 9d17bc92dcae9e906dfe18d7665fbf489d278234
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790861"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="70c85-102">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70c85-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="70c85-103">Načte informace o ladicím symbolu pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="70c85-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="70c85-104">Metody</span><span class="sxs-lookup"><span data-stu-id="70c85-104">Methods</span></span>  
  
|<span data-ttu-id="70c85-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="70c85-105">Method</span></span>|<span data-ttu-id="70c85-106">Popis</span><span class="sxs-lookup"><span data-stu-id="70c85-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="70c85-107">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="70c85-107">GetName Method</span></span>](icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="70c85-108">Získá název proměnné.</span><span class="sxs-lookup"><span data-stu-id="70c85-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="70c85-109">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="70c85-109">GetSize Method</span></span>](icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="70c85-110">Získá velikost proměnné v bajtech.</span><span class="sxs-lookup"><span data-stu-id="70c85-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="70c85-111">GetSlotIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="70c85-111">GetSlotIndex Method</span></span>](icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="70c85-112">Načte index spravovaného slotu místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="70c85-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="70c85-113">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="70c85-113">GetValue Method</span></span>](icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="70c85-114">Získá hodnotu proměnné jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="70c85-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="70c85-115">SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="70c85-115">SetValue Method</span></span>](icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="70c85-116">Přiřadí hodnotu bajtového pole proměnné.</span><span class="sxs-lookup"><span data-stu-id="70c85-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70c85-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70c85-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="70c85-118">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="70c85-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="70c85-119">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="70c85-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70c85-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70c85-120">Requirements</span></span>  
 <span data-ttu-id="70c85-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70c85-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70c85-122">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="70c85-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70c85-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="70c85-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70c85-124">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70c85-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70c85-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70c85-125">See also</span></span>

- [<span data-ttu-id="70c85-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="70c85-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="70c85-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="70c85-127">Debugging</span></span>](index.md)
