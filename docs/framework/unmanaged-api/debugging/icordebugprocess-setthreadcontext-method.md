---
title: ICorDebugProcess::SetThreadContext – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e281022cd7bc9b2095fdbd3964061b811ef60e0d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496960"
---
# <a name="icordebugprocesssetthreadcontext-method"></a><span data-ttu-id="e6d7d-102">ICorDebugProcess::SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="e6d7d-102">ICorDebugProcess::SetThreadContext Method</span></span>
<span data-ttu-id="e6d7d-103">Nastaví kontext pro dané vlákno v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="e6d7d-103">Sets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6d7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6d7d-104">Syntax</span></span>  
  
```  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6d7d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e6d7d-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="e6d7d-106">[in] ID vlákna, pro kterou chcete nastavit kontext.</span><span class="sxs-lookup"><span data-stu-id="e6d7d-106">[in] The ID of the thread for which to set the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="e6d7d-107">[in] Velikost `context` pole.</span><span class="sxs-lookup"><span data-stu-id="e6d7d-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="e6d7d-108">[in] Pole bajtů, které popisují kontext vlákna.</span><span class="sxs-lookup"><span data-stu-id="e6d7d-108">[in] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="e6d7d-109">Kontext určuje architekturu procesoru, na kterém vlákno prováděno.</span><span class="sxs-lookup"><span data-stu-id="e6d7d-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6d7d-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e6d7d-110">Remarks</span></span>  
 <span data-ttu-id="e6d7d-111">Ladicí program by měly volat tuto metodu, spíše než Win32 `SetThreadContext` fungovat, protože vlákno může být ve skutečnosti ve stavu "napadenému", ve kterém jeho kontext dočasně změnit.</span><span class="sxs-lookup"><span data-stu-id="e6d7d-111">The debugger should call this method rather than the Win32 `SetThreadContext` function, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="e6d7d-112">Tato metoda by měla sloužit pouze v případě vlákna v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="e6d7d-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="e6d7d-113">Použití [icordebugregisterset –](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) pro vlákna ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="e6d7d-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span> <span data-ttu-id="e6d7d-114">Nikdy by mělo stačit změnit kontext vlákna během ladění událost out-of-band (OOB).</span><span class="sxs-lookup"><span data-stu-id="e6d7d-114">You should never need to modify the context of a thread during an out-of-band (OOB) debug event.</span></span>  
  
 <span data-ttu-id="e6d7d-115">Data předaná musí být struktura kontext pro aktuální platformu.</span><span class="sxs-lookup"><span data-stu-id="e6d7d-115">The data passed must be a context structure for the current platform.</span></span>  
  
 <span data-ttu-id="e6d7d-116">Tato metoda můžou poškodit modul runtime, pokud používá nesprávně.</span><span class="sxs-lookup"><span data-stu-id="e6d7d-116">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6d7d-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e6d7d-117">Requirements</span></span>  
 <span data-ttu-id="e6d7d-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6d7d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6d7d-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e6d7d-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6d7d-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6d7d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6d7d-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6d7d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
