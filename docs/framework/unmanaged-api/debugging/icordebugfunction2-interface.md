---
title: ICorDebugFunction2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction2
helpviewer_keywords: ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 2b936bef-9b75-48bf-859f-42e419c65f1c
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ac3a4cd5ec2aff1b60cd51ca33d411e5cc81eb1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction2-interface1"></a><span data-ttu-id="f33dd-102">ICorDebugFunction2 Interface1</span><span class="sxs-lookup"><span data-stu-id="f33dd-102">ICorDebugFunction2 Interface1</span></span>
<span data-ttu-id="f33dd-103">Logicky rozšiřuje rozhraní ICorDebugFunction kvůli zajištění podpory pro pouze můj kód procházení po kroku ladění, který přeskočí bez uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="f33dd-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f33dd-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f33dd-104">Methods</span></span>  
  
|<span data-ttu-id="f33dd-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f33dd-105">Method</span></span>|<span data-ttu-id="f33dd-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f33dd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f33dd-107">EnumerateNativeCode – metoda</span><span class="sxs-lookup"><span data-stu-id="f33dd-107">EnumerateNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="f33dd-108">(Ještě nebyla implementována.) Získá ukazatele rozhraní umožňuje icordebugcodeenum –, který obsahuje příkazy nativního kódu ve funkci odkazuje tento objekt ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="f33dd-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="f33dd-109">GetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="f33dd-109">GetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="f33dd-110">Získá hodnotu, která určuje, zda tato funkce je označen jako uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="f33dd-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="f33dd-111">GetVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="f33dd-111">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="f33dd-112">Získá verzi aplikace upravit a pokračovat v této funkce.</span><span class="sxs-lookup"><span data-stu-id="f33dd-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="f33dd-113">SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="f33dd-113">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="f33dd-114">Tato funkce se pro pouze můj kód označí krokování s.</span><span class="sxs-lookup"><span data-stu-id="f33dd-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f33dd-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f33dd-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f33dd-116">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="f33dd-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f33dd-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f33dd-117">Requirements</span></span>  
 <span data-ttu-id="f33dd-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f33dd-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f33dd-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f33dd-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f33dd-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f33dd-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f33dd-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f33dd-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f33dd-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="f33dd-122">See Also</span></span>  
 [<span data-ttu-id="f33dd-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f33dd-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
