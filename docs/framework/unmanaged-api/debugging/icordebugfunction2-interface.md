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
ms.openlocfilehash: d051c7d61d6ade1fc0d313c47125d9c196bcca1d
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979578"
---
# <a name="icordebugfunction2-interface"></a><span data-ttu-id="44e53-102">ICorDebugFunction2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="44e53-102">ICorDebugFunction2 Interface</span></span>

<span data-ttu-id="44e53-103">Logicky rozšiřuje rozhraní ICorDebugFunction pro poskytnutí podpory pro volbu pouze vlastní kód krokové ladění, který přeskočí neuživatelský kód.</span><span class="sxs-lookup"><span data-stu-id="44e53-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="44e53-104">Metody</span><span class="sxs-lookup"><span data-stu-id="44e53-104">Methods</span></span>  
  
|<span data-ttu-id="44e53-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="44e53-105">Method</span></span>|<span data-ttu-id="44e53-106">Popis</span><span class="sxs-lookup"><span data-stu-id="44e53-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="44e53-107">EnumerateNativeCode – metoda</span><span class="sxs-lookup"><span data-stu-id="44e53-107">EnumerateNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="44e53-108">(Ještě nebyla implementována.) Získá ukazatel rozhraní icordebugcodeenum –, který obsahuje příkazy nativního kódu ve funkci odkazuje tento objekt icordebugfunction2 –.</span><span class="sxs-lookup"><span data-stu-id="44e53-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="44e53-109">GetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="44e53-109">GetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="44e53-110">Získá hodnotu, která indikuje, jestli tato funkce je označený jako uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="44e53-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="44e53-111">GetVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="44e53-111">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="44e53-112">Získá verzi této funkce upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="44e53-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="44e53-113">SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="44e53-113">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="44e53-114">Označí tato funkce pro volbu pouze vlastní kód krokování.</span><span class="sxs-lookup"><span data-stu-id="44e53-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44e53-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44e53-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44e53-116">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="44e53-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44e53-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="44e53-117">Requirements</span></span>  
 <span data-ttu-id="44e53-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44e53-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44e53-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44e53-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44e53-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44e53-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44e53-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44e53-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44e53-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44e53-122">See also</span></span>
- [<span data-ttu-id="44e53-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="44e53-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
