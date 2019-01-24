---
title: ICorDebugVariableSymbol Interface
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9822a3403c6ff738f7a6556a35cb383426575cb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582588"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="82789-102">ICorDebugVariableSymbol Interface</span><span class="sxs-lookup"><span data-stu-id="82789-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="82789-103">Načte informace o symbolu ladění pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="82789-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="82789-104">Metody</span><span class="sxs-lookup"><span data-stu-id="82789-104">Methods</span></span>  
  
|<span data-ttu-id="82789-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="82789-105">Method</span></span>|<span data-ttu-id="82789-106">Popis</span><span class="sxs-lookup"><span data-stu-id="82789-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="82789-107">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="82789-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="82789-108">Získá název proměnné.</span><span class="sxs-lookup"><span data-stu-id="82789-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="82789-109">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="82789-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="82789-110">Získá velikost proměnné v bajtech.</span><span class="sxs-lookup"><span data-stu-id="82789-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="82789-111">GetSlotIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="82789-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="82789-112">Získá index spravované slotu místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="82789-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="82789-113">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="82789-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="82789-114">Získá hodnotu proměnné jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="82789-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="82789-115">SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="82789-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="82789-116">Přiřadí hodnotu pole bajtů na proměnnou.</span><span class="sxs-lookup"><span data-stu-id="82789-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82789-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="82789-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82789-118">Toto rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="82789-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="82789-119">Pokud se rozhodnete implementovat toto rozhraní ICorDebug scénářích mimo .NET Native, modul common language runtime bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="82789-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82789-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="82789-120">Requirements</span></span>  
 <span data-ttu-id="82789-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82789-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82789-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82789-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82789-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82789-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82789-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82789-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82789-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82789-125">See also</span></span>
- [<span data-ttu-id="82789-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="82789-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="82789-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="82789-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
