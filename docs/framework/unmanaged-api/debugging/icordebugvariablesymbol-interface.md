---
title: ICorDebugVariableSymbol rozhraní
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73072dd9564853852b4d57e73c810680fdbcc4f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421334"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="2b096-102">ICorDebugVariableSymbol rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b096-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="2b096-103">Načte informace o ladění symbol pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="2b096-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2b096-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2b096-104">Methods</span></span>  
  
|<span data-ttu-id="2b096-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2b096-105">Method</span></span>|<span data-ttu-id="2b096-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2b096-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2b096-107">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="2b096-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="2b096-108">Získá název proměnné.</span><span class="sxs-lookup"><span data-stu-id="2b096-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="2b096-109">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="2b096-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="2b096-110">Získá velikost proměnné v bajtech.</span><span class="sxs-lookup"><span data-stu-id="2b096-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="2b096-111">GetSlotIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="2b096-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="2b096-112">Získá index spravované slotu místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="2b096-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="2b096-113">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="2b096-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="2b096-114">Získá hodnotu proměnné jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="2b096-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="2b096-115">SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="2b096-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="2b096-116">Proměnné přiřazuje hodnoty bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="2b096-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b096-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b096-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b096-118">Toto rozhraní je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="2b096-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="2b096-119">Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2b096-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b096-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2b096-120">Requirements</span></span>  
 <span data-ttu-id="2b096-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b096-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b096-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b096-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b096-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b096-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b096-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b096-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b096-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="2b096-125">See Also</span></span>  
 [<span data-ttu-id="2b096-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2b096-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="2b096-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="2b096-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
