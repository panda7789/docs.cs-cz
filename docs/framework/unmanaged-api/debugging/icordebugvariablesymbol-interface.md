---
title: ICorDebugVariableSymbol – rozhraní
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
ms.openlocfilehash: 412ecbfc03378947e5a578e163034d104718bc91
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397095"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="2afd7-102">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2afd7-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="2afd7-103">Načte informace o ladicím symbolu pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="2afd7-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2afd7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2afd7-104">Methods</span></span>  
  
|<span data-ttu-id="2afd7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2afd7-105">Method</span></span>|<span data-ttu-id="2afd7-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2afd7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2afd7-107">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="2afd7-107">GetName Method</span></span>](icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="2afd7-108">Získá název proměnné.</span><span class="sxs-lookup"><span data-stu-id="2afd7-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="2afd7-109">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="2afd7-109">GetSize Method</span></span>](icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="2afd7-110">Získá velikost proměnné v bajtech.</span><span class="sxs-lookup"><span data-stu-id="2afd7-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="2afd7-111">GetSlotIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="2afd7-111">GetSlotIndex Method</span></span>](icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="2afd7-112">Načte index spravovaného slotu místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="2afd7-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="2afd7-113">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="2afd7-113">GetValue Method</span></span>](icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="2afd7-114">Získá hodnotu proměnné jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="2afd7-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="2afd7-115">SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="2afd7-115">SetValue Method</span></span>](icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="2afd7-116">Přiřadí hodnotu bajtového pole proměnné.</span><span class="sxs-lookup"><span data-stu-id="2afd7-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2afd7-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2afd7-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2afd7-118">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2afd7-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="2afd7-119">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="2afd7-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2afd7-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2afd7-120">Requirements</span></span>  
 <span data-ttu-id="2afd7-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2afd7-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2afd7-122">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2afd7-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2afd7-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2afd7-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2afd7-124">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2afd7-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2afd7-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="2afd7-125">See also</span></span>

- [<span data-ttu-id="2afd7-126">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2afd7-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2afd7-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="2afd7-127">Debugging</span></span>](index.md)
