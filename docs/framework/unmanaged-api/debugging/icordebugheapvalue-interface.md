---
title: ICorDebugHeapValue – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue
helpviewer_keywords:
- ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5263474b7b5001d561652291c23220da0a942bd1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980565"
---
# <a name="icordebugheapvalue-interface"></a><span data-ttu-id="69bc8-102">ICorDebugHeapValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="69bc8-102">ICorDebugHeapValue Interface</span></span>

<span data-ttu-id="69bc8-103">Podtřída ICorDebugValue"", který představuje objekt, který byl shromážděn uvolňováním paměti common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="69bc8-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="69bc8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="69bc8-104">Methods</span></span>  
  
|<span data-ttu-id="69bc8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="69bc8-105">Method</span></span>|<span data-ttu-id="69bc8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="69bc8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="69bc8-107">CreateRelocBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="69bc8-107">CreateRelocBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="69bc8-108">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="69bc8-108">Not implemented.</span></span>|  
|[<span data-ttu-id="69bc8-109">IsValid – metoda</span><span class="sxs-lookup"><span data-stu-id="69bc8-109">IsValid Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="69bc8-110">Získá hodnotu určující, zda objekt reprezentovaný tímto objektem `ICorDebugHeapValue` je platný, nebo byl uvolněn systémem uvolňování.</span><span class="sxs-lookup"><span data-stu-id="69bc8-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="69bc8-111">Tato metoda je zastaralá v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="69bc8-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69bc8-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="69bc8-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69bc8-113">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="69bc8-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69bc8-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="69bc8-114">Requirements</span></span>  
 <span data-ttu-id="69bc8-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69bc8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69bc8-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69bc8-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69bc8-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69bc8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69bc8-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69bc8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69bc8-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69bc8-119">See also</span></span>



- [<span data-ttu-id="69bc8-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="69bc8-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
