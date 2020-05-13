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
ms.openlocfilehash: 611091d39da6d7f646457457f20ce1eaf37db361
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213202"
---
# <a name="icordebugfunction2-interface"></a><span data-ttu-id="8230d-102">ICorDebugFunction2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8230d-102">ICorDebugFunction2 Interface</span></span>

<span data-ttu-id="8230d-103">Logicky rozšiřuje rozhraní ICorDebugFunction, aby poskytovala podporu pro Pouze můj kód krok po ladění, které přeskočí jiný než uživatelský kód.</span><span class="sxs-lookup"><span data-stu-id="8230d-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8230d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8230d-104">Methods</span></span>  
  
|<span data-ttu-id="8230d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8230d-105">Method</span></span>|<span data-ttu-id="8230d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8230d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8230d-107">EnumerateNativeCode – metoda</span><span class="sxs-lookup"><span data-stu-id="8230d-107">EnumerateNativeCode Method</span></span>](icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="8230d-108">(Ještě není implementováno.) Získá ukazatel rozhraní na ICorDebugCodeEnum, který obsahuje příkazy nativního kódu ve funkci, na kterou odkazuje tento objekt ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="8230d-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="8230d-109">GetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="8230d-109">GetJMCStatus Method</span></span>](icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="8230d-110">Získá hodnotu, která označuje, zda je tato funkce označena jako uživatelský kód.</span><span class="sxs-lookup"><span data-stu-id="8230d-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="8230d-111">GetVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="8230d-111">GetVersionNumber Method</span></span>](icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="8230d-112">Získá verzi této funkce pro úpravu a pokračování.</span><span class="sxs-lookup"><span data-stu-id="8230d-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="8230d-113">SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="8230d-113">SetJMCStatus Method</span></span>](icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="8230d-114">Označuje tuto funkci pro Pouze můj kód krokování.</span><span class="sxs-lookup"><span data-stu-id="8230d-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8230d-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8230d-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8230d-116">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="8230d-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8230d-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8230d-117">Requirements</span></span>  
 <span data-ttu-id="8230d-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8230d-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8230d-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8230d-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8230d-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8230d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8230d-121">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8230d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8230d-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="8230d-122">See also</span></span>

- [<span data-ttu-id="8230d-123">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8230d-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
