---
title: "ICorDebug::Terminate – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.Terminate
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::Terminate
helpviewer_keywords:
- Terminate method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Terminate method [.NET Framework debugging]
ms.assetid: fffe5616-0896-4426-ab5e-21869b514883
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b18bb6222296c5e8875f983d47118f938a54bcc2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="082e2-102">ICorDebug::Terminate – metoda</span><span class="sxs-lookup"><span data-stu-id="082e2-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="082e2-103">Ukončí `ICorDebug` objektu.</span><span class="sxs-lookup"><span data-stu-id="082e2-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="082e2-104">`Terminate`nelze volat až [icordebugmanagedcallback::exitprocess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) zpětného volání byla přijata pro všechny procesy laděné.</span><span class="sxs-lookup"><span data-stu-id="082e2-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="082e2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="082e2-105">Syntax</span></span>  
  
```  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="082e2-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="082e2-106">Remarks</span></span>  
 <span data-ttu-id="082e2-107">`Terminate`musí být voláno, když `ICorDebug` objekt již není potřeba.</span><span class="sxs-lookup"><span data-stu-id="082e2-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="082e2-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="082e2-108">Requirements</span></span>  
 <span data-ttu-id="082e2-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="082e2-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="082e2-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="082e2-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="082e2-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="082e2-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="082e2-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="082e2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="082e2-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="082e2-113">See Also</span></span>  
 [<span data-ttu-id="082e2-114">ICorDebug – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="082e2-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
