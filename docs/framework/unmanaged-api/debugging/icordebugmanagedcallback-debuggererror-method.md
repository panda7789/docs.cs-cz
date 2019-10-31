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
ms.openlocfilehash: c03be2405e1ab0287a2921b6e2e293862c67a193
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137376"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="7d39f-102">ICorDebugManagedCallback::DebuggerError – metoda</span><span class="sxs-lookup"><span data-stu-id="7d39f-102">ICorDebugManagedCallback::DebuggerError Method</span></span>
<span data-ttu-id="7d39f-103">Oznamuje ladicímu programu, že došlo k chybě při pokusu o zpracování události ze společného jazykového modulu runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="7d39f-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d39f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d39f-104">Syntax</span></span>  
  
```cpp  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d39f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d39f-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="7d39f-106">pro Ukazatel na objekt "ICorDebugProcess", který představuje proces, ve kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="7d39f-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="7d39f-107">pro Hodnota HRESULT, která byla vrácena z obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="7d39f-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="7d39f-108">pro Celé číslo, které určuje chybu CLR.</span><span class="sxs-lookup"><span data-stu-id="7d39f-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d39f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d39f-109">Remarks</span></span>  
 <span data-ttu-id="7d39f-110">Tento proces může být umístěn do předávacího režimu v závislosti na povaze chyby.</span><span class="sxs-lookup"><span data-stu-id="7d39f-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="7d39f-111">`DebugError` zpětné volání indikuje, že služby ladění byly kvůli chybě zakázané, takže ladicí program by měl uživatelům zpřístupnit chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="7d39f-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="7d39f-112">[ICorDebugProcess:: getId –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) bude bezpečné volat, ale žádné jiné metody, včetně [ICorDebug:: Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), by neměly být volány.</span><span class="sxs-lookup"><span data-stu-id="7d39f-112">[ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="7d39f-113">Ladicí program by měl pro ukončení procesů používat zařízení s operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="7d39f-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d39f-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d39f-114">Requirements</span></span>  
 <span data-ttu-id="7d39f-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d39f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d39f-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7d39f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d39f-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7d39f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d39f-118">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d39f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d39f-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d39f-119">See also</span></span>

- [<span data-ttu-id="7d39f-120">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d39f-120">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
