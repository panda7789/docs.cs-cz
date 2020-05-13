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
ms.openlocfilehash: 8f3697f8b193319ebb7b155ad79b8ec25a0a2266
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205274"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="08797-102">ICorDebugManagedCallback::DebuggerError – metoda</span><span class="sxs-lookup"><span data-stu-id="08797-102">ICorDebugManagedCallback::DebuggerError Method</span></span>
<span data-ttu-id="08797-103">Oznamuje ladicímu programu, že došlo k chybě při pokusu o zpracování události ze společného jazykového modulu runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="08797-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08797-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08797-104">Syntax</span></span>  
  
```cpp  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08797-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="08797-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="08797-106">pro Ukazatel na objekt "ICorDebugProcess", který představuje proces, ve kterém došlo k události.</span><span class="sxs-lookup"><span data-stu-id="08797-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="08797-107">pro Hodnota HRESULT, která byla vrácena z obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="08797-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="08797-108">pro Celé číslo, které určuje chybu CLR.</span><span class="sxs-lookup"><span data-stu-id="08797-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08797-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="08797-109">Remarks</span></span>  
 <span data-ttu-id="08797-110">Tento proces může být umístěn do předávacího režimu v závislosti na povaze chyby.</span><span class="sxs-lookup"><span data-stu-id="08797-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="08797-111">`DebugError`Zpětné volání indikuje, že služby ladění byly kvůli chybě zakázané, takže ladicí program by měl uživatelům zpřístupnit chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="08797-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="08797-112">[ICorDebugProcess:: getId –](icordebugprocess-getid-method.md) bude bezpečné volat, ale žádné jiné metody, včetně [ICorDebug:: Terminate](icordebug-terminate-method.md), by neměly být volány.</span><span class="sxs-lookup"><span data-stu-id="08797-112">[ICorDebugProcess::GetID](icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="08797-113">Ladicí program by měl pro ukončení procesů používat zařízení s operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="08797-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08797-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="08797-114">Requirements</span></span>  
 <span data-ttu-id="08797-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08797-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08797-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="08797-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08797-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="08797-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08797-118">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08797-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08797-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="08797-119">See also</span></span>

- [<span data-ttu-id="08797-120">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="08797-120">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
