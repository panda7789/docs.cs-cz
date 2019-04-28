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
ms.openlocfilehash: 159cebc76f732629ed84a3b6c9041cc15f8bbb69
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763760"
---
# <a name="icordebugfunction2-interface"></a><span data-ttu-id="58b98-102">ICorDebugFunction2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="58b98-102">ICorDebugFunction2 Interface</span></span>

<span data-ttu-id="58b98-103">Logicky rozšiřuje rozhraní ICorDebugFunction pro poskytnutí podpory pro volbu pouze vlastní kód krokové ladění, který přeskočí neuživatelský kód.</span><span class="sxs-lookup"><span data-stu-id="58b98-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="58b98-104">Metody</span><span class="sxs-lookup"><span data-stu-id="58b98-104">Methods</span></span>  
  
|<span data-ttu-id="58b98-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="58b98-105">Method</span></span>|<span data-ttu-id="58b98-106">Popis</span><span class="sxs-lookup"><span data-stu-id="58b98-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="58b98-107">EnumerateNativeCode – metoda</span><span class="sxs-lookup"><span data-stu-id="58b98-107">EnumerateNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="58b98-108">(Ještě nebyla implementována.) Získá ukazatel rozhraní icordebugcodeenum –, který obsahuje příkazy nativního kódu ve funkci odkazuje tento objekt icordebugfunction2 –.</span><span class="sxs-lookup"><span data-stu-id="58b98-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="58b98-109">GetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="58b98-109">GetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="58b98-110">Získá hodnotu, která indikuje, jestli tato funkce je označený jako uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="58b98-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="58b98-111">GetVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="58b98-111">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="58b98-112">Získá verzi této funkce upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="58b98-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="58b98-113">SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="58b98-113">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="58b98-114">Označí tato funkce pro volbu pouze vlastní kód krokování.</span><span class="sxs-lookup"><span data-stu-id="58b98-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58b98-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="58b98-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58b98-116">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="58b98-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58b98-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="58b98-117">Requirements</span></span>  
 <span data-ttu-id="58b98-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58b98-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58b98-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58b98-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58b98-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58b98-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58b98-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58b98-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58b98-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58b98-122">See also</span></span>

- [<span data-ttu-id="58b98-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="58b98-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
