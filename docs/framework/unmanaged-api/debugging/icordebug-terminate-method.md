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
ms.openlocfilehash: 057ee7a323a8a725ebf82ee9dbaea61a43c061ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674606"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="f45e9-102">ICorDebug::Terminate – metoda</span><span class="sxs-lookup"><span data-stu-id="f45e9-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="f45e9-103">Ukončuje `ICorDebug` objektu.</span><span class="sxs-lookup"><span data-stu-id="f45e9-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f45e9-104">`Terminate` by neměla být volána až [icordebugmanagedcallback::exitprocess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) byla přijata zpětného volání pro všechny procesy, které jsou právě laděny.</span><span class="sxs-lookup"><span data-stu-id="f45e9-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f45e9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f45e9-105">Syntax</span></span>  
  
```  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f45e9-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f45e9-106">Remarks</span></span>  
 <span data-ttu-id="f45e9-107">`Terminate` musí být voláno, když `ICorDebug` objekt už nebude potřeba.</span><span class="sxs-lookup"><span data-stu-id="f45e9-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f45e9-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f45e9-108">Requirements</span></span>  
 <span data-ttu-id="f45e9-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f45e9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f45e9-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f45e9-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f45e9-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f45e9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f45e9-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f45e9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f45e9-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f45e9-113">See also</span></span>
- [<span data-ttu-id="f45e9-114">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f45e9-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
