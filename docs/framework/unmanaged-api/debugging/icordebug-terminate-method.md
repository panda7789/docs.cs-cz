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
ms.openlocfilehash: 78838e9002cb3f5263395af9de255c54de47b6ae
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134021"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="fb507-102">ICorDebug::Terminate – metoda</span><span class="sxs-lookup"><span data-stu-id="fb507-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="fb507-103">Ukončí objekt `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="fb507-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fb507-104">`Terminate` by neměl být voláno, dokud nebylo přijato zpětné volání [ICorDebugManagedCallback:: ExitProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) pro všechny laděné procesy.</span><span class="sxs-lookup"><span data-stu-id="fb507-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb507-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb507-105">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="fb507-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb507-106">Remarks</span></span>  
 <span data-ttu-id="fb507-107">`Terminate` musí být volána, pokud již není objekt `ICorDebug` potřeba.</span><span class="sxs-lookup"><span data-stu-id="fb507-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb507-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb507-108">Requirements</span></span>  
 <span data-ttu-id="fb507-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb507-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb507-110">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fb507-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb507-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fb507-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb507-112">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb507-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb507-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb507-113">See also</span></span>

- [<span data-ttu-id="fb507-114">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb507-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
