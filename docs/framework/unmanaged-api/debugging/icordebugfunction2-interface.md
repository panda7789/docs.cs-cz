---
title: ICorDebugFunction2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2
helpviewer_keywords:
- ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 2b936bef-9b75-48bf-859f-42e419c65f1c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a4349ad4dbaeafa63689ef85a307211428f8538
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917093"
---
# <a name="icordebugfunction2-interface"></a><span data-ttu-id="b1f44-102">ICorDebugFunction2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b1f44-102">ICorDebugFunction2 Interface</span></span>

<span data-ttu-id="b1f44-103">Logicky rozšiřuje rozhraní ICorDebugFunction, aby poskytovala podporu pro Pouze můj kód krok po ladění, které přeskočí jiný než uživatelský kód.</span><span class="sxs-lookup"><span data-stu-id="b1f44-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b1f44-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b1f44-104">Methods</span></span>  
  
|<span data-ttu-id="b1f44-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b1f44-105">Method</span></span>|<span data-ttu-id="b1f44-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b1f44-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b1f44-107">EnumerateNativeCode – metoda</span><span class="sxs-lookup"><span data-stu-id="b1f44-107">EnumerateNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="b1f44-108">(Ještě není implementováno.) Získá ukazatel rozhraní na ICorDebugCodeEnum, který obsahuje příkazy nativního kódu ve funkci, na kterou odkazuje tento objekt ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="b1f44-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="b1f44-109">GetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="b1f44-109">GetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="b1f44-110">Získá hodnotu, která označuje, zda je tato funkce označena jako uživatelský kód.</span><span class="sxs-lookup"><span data-stu-id="b1f44-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="b1f44-111">GetVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="b1f44-111">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="b1f44-112">Získá verzi této funkce pro úpravu a pokračování.</span><span class="sxs-lookup"><span data-stu-id="b1f44-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="b1f44-113">SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="b1f44-113">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="b1f44-114">Označuje tuto funkci pro Pouze můj kód krokování.</span><span class="sxs-lookup"><span data-stu-id="b1f44-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1f44-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1f44-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1f44-116">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="b1f44-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1f44-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1f44-117">Requirements</span></span>  
 <span data-ttu-id="b1f44-118">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1f44-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1f44-119">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b1f44-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1f44-120">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1f44-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1f44-121">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1f44-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1f44-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1f44-122">See also</span></span>

- [<span data-ttu-id="b1f44-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b1f44-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
