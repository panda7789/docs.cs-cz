---
title: ICorDebugManagedCallback::LoadModule – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbf538f066058b4f80d8cfd6cdf1a79683c79be9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413414"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="93176-102">ICorDebugManagedCallback::LoadModule – metoda</span><span class="sxs-lookup"><span data-stu-id="93176-102">ICorDebugManagedCallback::LoadModule Method</span></span>
<span data-ttu-id="93176-103">Upozorní ladicí program úspěšně načtena společný modul runtime (CLR) jazyk.</span><span class="sxs-lookup"><span data-stu-id="93176-103">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93176-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93176-104">Syntax</span></span>  
  
```  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93176-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="93176-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="93176-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace, do kterého se načetl modul.</span><span class="sxs-lookup"><span data-stu-id="93176-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="93176-107">[v] Ukazatel na ICorDebugModule objekt, který reprezentuje modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="93176-107">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93176-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93176-108">Remarks</span></span>  
 <span data-ttu-id="93176-109">`LoadModule` Zpětné volání poskytuje příslušnou dobu prozkoumat metadata pro modul, nastavte příznaky kompilátoru za běhu (JIT), nebo povolit nebo zakázat třídy načítání zpětných volání pro modul.</span><span class="sxs-lookup"><span data-stu-id="93176-109">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93176-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="93176-110">Requirements</span></span>  
 <span data-ttu-id="93176-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93176-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93176-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93176-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93176-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93176-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93176-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93176-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93176-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="93176-115">See Also</span></span>  
 [<span data-ttu-id="93176-116">UnloadModule – metoda</span><span class="sxs-lookup"><span data-stu-id="93176-116">UnloadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)  
 [<span data-ttu-id="93176-117">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93176-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
