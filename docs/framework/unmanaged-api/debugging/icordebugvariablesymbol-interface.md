---
title: ICorDebugVariableSymbol – rozhraní
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c7cdababd1e4b5fae4f5e48a654f861b708a6e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226557"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="5fb85-102">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5fb85-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="5fb85-103">Načte informace o symbolu ladění pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="5fb85-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5fb85-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5fb85-104">Methods</span></span>  
  
|<span data-ttu-id="5fb85-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5fb85-105">Method</span></span>|<span data-ttu-id="5fb85-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5fb85-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5fb85-107">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="5fb85-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="5fb85-108">Získá název proměnné.</span><span class="sxs-lookup"><span data-stu-id="5fb85-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="5fb85-109">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="5fb85-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="5fb85-110">Získá velikost proměnné v bajtech.</span><span class="sxs-lookup"><span data-stu-id="5fb85-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="5fb85-111">GetSlotIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="5fb85-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="5fb85-112">Získá index spravované slotu místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="5fb85-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="5fb85-113">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="5fb85-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="5fb85-114">Získá hodnotu proměnné jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="5fb85-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="5fb85-115">SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="5fb85-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="5fb85-116">Přiřadí hodnotu pole bajtů na proměnnou.</span><span class="sxs-lookup"><span data-stu-id="5fb85-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fb85-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5fb85-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5fb85-118">Toto rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5fb85-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="5fb85-119">Pokud se rozhodnete implementovat toto rozhraní ICorDebug scénářích mimo .NET Native, modul common language runtime bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5fb85-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fb85-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5fb85-120">Requirements</span></span>  
 <span data-ttu-id="5fb85-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fb85-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fb85-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5fb85-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fb85-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5fb85-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5fb85-124">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5fb85-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5fb85-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5fb85-125">See also</span></span>

- [<span data-ttu-id="5fb85-126">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5fb85-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="5fb85-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="5fb85-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
