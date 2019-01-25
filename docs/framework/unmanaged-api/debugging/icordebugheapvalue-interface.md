---
title: ICorDebugHeapValue Interface1
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
ms.openlocfilehash: a87790647ed8896f072aa8e943e31fa1980e3f62
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622855"
---
# <a name="icordebugheapvalue-interface1"></a><span data-ttu-id="879f7-102">ICorDebugHeapValue Interface1</span><span class="sxs-lookup"><span data-stu-id="879f7-102">ICorDebugHeapValue Interface1</span></span>
<span data-ttu-id="879f7-103">Podtřída ICorDebugValue"", který představuje objekt, který byl shromážděn uvolňováním paměti common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="879f7-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="879f7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="879f7-104">Methods</span></span>  
  
|<span data-ttu-id="879f7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="879f7-105">Method</span></span>|<span data-ttu-id="879f7-106">Popis</span><span class="sxs-lookup"><span data-stu-id="879f7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="879f7-107">CreateRelocBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="879f7-107">CreateRelocBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="879f7-108">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="879f7-108">Not implemented.</span></span>|  
|[<span data-ttu-id="879f7-109">IsValid – metoda</span><span class="sxs-lookup"><span data-stu-id="879f7-109">IsValid Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="879f7-110">Získá hodnotu určující, zda objekt reprezentovaný tímto objektem `ICorDebugHeapValue` je platný, nebo byl uvolněn systémem uvolňování.</span><span class="sxs-lookup"><span data-stu-id="879f7-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="879f7-111">Tato metoda je zastaralá v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="879f7-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="879f7-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="879f7-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="879f7-113">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="879f7-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="879f7-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="879f7-114">Requirements</span></span>  
 <span data-ttu-id="879f7-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="879f7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="879f7-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="879f7-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="879f7-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="879f7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="879f7-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="879f7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="879f7-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="879f7-119">See also</span></span>



- [<span data-ttu-id="879f7-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="879f7-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
