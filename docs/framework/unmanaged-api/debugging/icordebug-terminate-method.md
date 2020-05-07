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
ms.openlocfilehash: 44bb98f54debb129f951cc388fea81ca0f17b20c
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895311"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="92c17-102">ICorDebug::Terminate – metoda</span><span class="sxs-lookup"><span data-stu-id="92c17-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="92c17-103">Ukončí `ICorDebug` objekt.</span><span class="sxs-lookup"><span data-stu-id="92c17-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92c17-104">`Terminate`neměl by být volána, dokud nebylo přijato zpětné volání [ICorDebugManagedCallback:: ExitProcess –](icordebugmanagedcallback-exitprocess-method.md) pro všechny laděné procesy.</span><span class="sxs-lookup"><span data-stu-id="92c17-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92c17-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92c17-105">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="92c17-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="92c17-106">Remarks</span></span>  
 <span data-ttu-id="92c17-107">`Terminate`musí být volána, když `ICorDebug` objekt již není potřeba.</span><span class="sxs-lookup"><span data-stu-id="92c17-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92c17-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="92c17-108">Requirements</span></span>  
 <span data-ttu-id="92c17-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92c17-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92c17-110">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="92c17-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92c17-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="92c17-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92c17-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92c17-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92c17-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="92c17-113">See also</span></span>

- [<span data-ttu-id="92c17-114">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92c17-114">ICorDebug Interface</span></span>](icordebug-interface.md)
