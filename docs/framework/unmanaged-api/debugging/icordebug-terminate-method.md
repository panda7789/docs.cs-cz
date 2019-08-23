---
title: ICorDebug::Terminate – metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Terminate
helpviewer_keywords:
- Terminate method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Terminate method [.NET Framework debugging]
ms.assetid: fffe5616-0896-4426-ab5e-21869b514883
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de37bb34aee9b6536ff892ac30855761bcc69445
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963133"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="e2513-102">ICorDebug::Terminate – metoda</span><span class="sxs-lookup"><span data-stu-id="e2513-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="e2513-103">`ICorDebug` Ukončí objekt.</span><span class="sxs-lookup"><span data-stu-id="e2513-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2513-104">`Terminate`neměl by být volána, dokud nebylo přijato zpětné volání [ICorDebugManagedCallback:: ExitProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) pro všechny laděné procesy.</span><span class="sxs-lookup"><span data-stu-id="e2513-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2513-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2513-105">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="e2513-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2513-106">Remarks</span></span>  
 <span data-ttu-id="e2513-107">`Terminate`musí být volána, když `ICorDebug` objekt již není potřeba.</span><span class="sxs-lookup"><span data-stu-id="e2513-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2513-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2513-108">Requirements</span></span>  
 <span data-ttu-id="e2513-109">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2513-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2513-110">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e2513-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2513-111">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2513-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2513-112">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2513-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2513-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2513-113">See also</span></span>

- [<span data-ttu-id="e2513-114">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2513-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
