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
ms.openlocfilehash: e6abc4893ac99c5ce93a409a8120f090250be57c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759662"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="b51fe-102">ICorDebugManagedCallback::DebuggerError – metoda</span><span class="sxs-lookup"><span data-stu-id="b51fe-102">ICorDebugManagedCallback::DebuggerError Method</span></span>
<span data-ttu-id="b51fe-103">Upozorní ladicího programu, že došlo k chybě při pokusu o zpracování události z common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="b51fe-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b51fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b51fe-104">Syntax</span></span>  
  
```cpp  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b51fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b51fe-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="b51fe-106">[in] Ukazatel na objekt "ICorDebugProcess", který představuje proces, ve kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="b51fe-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="b51fe-107">[in] Hodnota HRESULT, která byla vrácena z obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="b51fe-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="b51fe-108">[in] Celé číslo, které určuje chyba CLR.</span><span class="sxs-lookup"><span data-stu-id="b51fe-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b51fe-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b51fe-109">Remarks</span></span>  
 <span data-ttu-id="b51fe-110">Proces můžete umístit do režimu průchodu, v závislosti na povaze chyby.</span><span class="sxs-lookup"><span data-stu-id="b51fe-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="b51fe-111">`DebugError` Zpětného volání znamená, že ladění služby z důvodu chyby, byly zakázány, ladicí programy musí zpřístupnit chybová zpráva pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="b51fe-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="b51fe-112">[Icordebugprocess::getid –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) budou bezpečné i volání, ale všechny ostatní metody, včetně [icordebug::Terminate –](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), by neměla být volána.</span><span class="sxs-lookup"><span data-stu-id="b51fe-112">[ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="b51fe-113">Ladicí program používejte operačního systému zařízení ukončování procesů.</span><span class="sxs-lookup"><span data-stu-id="b51fe-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b51fe-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b51fe-114">Requirements</span></span>  
 <span data-ttu-id="b51fe-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b51fe-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b51fe-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b51fe-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b51fe-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b51fe-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b51fe-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b51fe-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b51fe-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b51fe-119">See also</span></span>

- [<span data-ttu-id="b51fe-120">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b51fe-120">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
