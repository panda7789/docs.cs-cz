---
title: ICorDebugManagedCallback::DebuggerError – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.DebuggerError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25af2c8fa3e3d49b3c2832a69f14b2691585d775
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489845"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="451d3-102">ICorDebugManagedCallback::DebuggerError – metoda</span><span class="sxs-lookup"><span data-stu-id="451d3-102">ICorDebugManagedCallback::DebuggerError Method</span></span>
<span data-ttu-id="451d3-103">Upozorní ladicího programu, že došlo k chybě při pokusu o zpracování události z common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="451d3-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="451d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="451d3-104">Syntax</span></span>  
  
```  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="451d3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="451d3-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="451d3-106">[in] Ukazatel na objekt "ICorDebugProcess", který představuje proces, ve kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="451d3-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="451d3-107">[in] Hodnota HRESULT, která byla vrácena z obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="451d3-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="451d3-108">[in] Celé číslo, které určuje chyba CLR.</span><span class="sxs-lookup"><span data-stu-id="451d3-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="451d3-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="451d3-109">Remarks</span></span>  
 <span data-ttu-id="451d3-110">Proces můžete umístit do režimu průchodu, v závislosti na povaze chyby.</span><span class="sxs-lookup"><span data-stu-id="451d3-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="451d3-111">`DebugError` Zpětného volání znamená, že ladění služby z důvodu chyby, byly zakázány, ladicí programy musí zpřístupnit chybová zpráva pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="451d3-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="451d3-112">[Icordebugprocess::getid –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) budou bezpečné i volání, ale všechny ostatní metody, včetně [icordebug::Terminate –](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), by neměla být volána.</span><span class="sxs-lookup"><span data-stu-id="451d3-112">[ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="451d3-113">Ladicí program používejte operačního systému zařízení ukončování procesů.</span><span class="sxs-lookup"><span data-stu-id="451d3-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="451d3-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="451d3-114">Requirements</span></span>  
 <span data-ttu-id="451d3-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="451d3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="451d3-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="451d3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="451d3-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="451d3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="451d3-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="451d3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="451d3-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="451d3-119">See also</span></span>
- [<span data-ttu-id="451d3-120">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="451d3-120">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
