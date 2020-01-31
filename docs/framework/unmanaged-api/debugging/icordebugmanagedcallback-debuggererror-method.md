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
ms.openlocfilehash: 9b96c0a2eca543b9e01ccf92b271b1aa7003c5c9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781939"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="81765-102">ICorDebugManagedCallback::DebuggerError – metoda</span><span class="sxs-lookup"><span data-stu-id="81765-102">ICorDebugManagedCallback::DebuggerError Method</span></span>
<span data-ttu-id="81765-103">Oznamuje ladicímu programu, že došlo k chybě při pokusu o zpracování události ze společného jazykového modulu runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="81765-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81765-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81765-104">Syntax</span></span>  
  
```cpp  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81765-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81765-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="81765-106">pro Ukazatel na objekt "ICorDebugProcess", který představuje proces, ve kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="81765-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="81765-107">pro Hodnota HRESULT, která byla vrácena z obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="81765-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="81765-108">pro Celé číslo, které určuje chybu CLR.</span><span class="sxs-lookup"><span data-stu-id="81765-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81765-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81765-109">Remarks</span></span>  
 <span data-ttu-id="81765-110">Tento proces může být umístěn do předávacího režimu v závislosti na povaze chyby.</span><span class="sxs-lookup"><span data-stu-id="81765-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="81765-111">`DebugError` zpětné volání indikuje, že služby ladění byly kvůli chybě zakázané, takže ladicí program by měl uživatelům zpřístupnit chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="81765-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="81765-112">[ICorDebugProcess:: getId –](icordebugprocess-getid-method.md) bude bezpečné volat, ale žádné jiné metody, včetně [ICorDebug:: Terminate](icordebug-terminate-method.md), by neměly být volány.</span><span class="sxs-lookup"><span data-stu-id="81765-112">[ICorDebugProcess::GetID](icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="81765-113">Ladicí program by měl pro ukončení procesů používat zařízení s operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="81765-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81765-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="81765-114">Requirements</span></span>  
 <span data-ttu-id="81765-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81765-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81765-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="81765-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81765-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="81765-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81765-118">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81765-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81765-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81765-119">See also</span></span>

- [<span data-ttu-id="81765-120">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="81765-120">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
