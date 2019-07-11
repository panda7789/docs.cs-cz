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
ms.openlocfilehash: 3037fc704ffc3aac4d050cef7857261f138f7d35
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738068"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="685d5-102">ICorDebug::Terminate – metoda</span><span class="sxs-lookup"><span data-stu-id="685d5-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="685d5-103">Ukončuje `ICorDebug` objektu.</span><span class="sxs-lookup"><span data-stu-id="685d5-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="685d5-104">`Terminate` by neměla být volána až [icordebugmanagedcallback::exitprocess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) byla přijata zpětného volání pro všechny procesy, které jsou právě laděny.</span><span class="sxs-lookup"><span data-stu-id="685d5-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="685d5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="685d5-105">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="685d5-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="685d5-106">Remarks</span></span>  
 <span data-ttu-id="685d5-107">`Terminate` musí být voláno, když `ICorDebug` objekt už nebude potřeba.</span><span class="sxs-lookup"><span data-stu-id="685d5-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="685d5-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="685d5-108">Requirements</span></span>  
 <span data-ttu-id="685d5-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="685d5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="685d5-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="685d5-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="685d5-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="685d5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="685d5-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="685d5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="685d5-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="685d5-113">See also</span></span>

- [<span data-ttu-id="685d5-114">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="685d5-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
