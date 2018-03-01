---
title: "ICorDebugProcess::SetThreadContext – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a7d40d455ea17b8df2acd77a1222ac6b080116c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocesssetthreadcontext-method"></a><span data-ttu-id="7bf20-102">ICorDebugProcess::SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="7bf20-102">ICorDebugProcess::SetThreadContext Method</span></span>
<span data-ttu-id="7bf20-103">Nastaví kontext pro dané vlákno v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="7bf20-103">Sets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bf20-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7bf20-104">Syntax</span></span>  
  
```  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7bf20-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7bf20-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="7bf20-106">[v] ID vlákna, pro kterou chcete nastavit kontext.</span><span class="sxs-lookup"><span data-stu-id="7bf20-106">[in] The ID of the thread for which to set the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="7bf20-107">[v] Velikost `context` pole.</span><span class="sxs-lookup"><span data-stu-id="7bf20-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="7bf20-108">[v] Pole bajtů, které popisují obsah podprocesu.</span><span class="sxs-lookup"><span data-stu-id="7bf20-108">[in] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="7bf20-109">Kontext určuje architekturu procesoru, na kterém je prováděna vlákno.</span><span class="sxs-lookup"><span data-stu-id="7bf20-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7bf20-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7bf20-110">Remarks</span></span>  
 <span data-ttu-id="7bf20-111">Ladicí program by měly volat tuto metodu, nikoli Win32 `SetThreadContext` fungovat, protože vlákno ve skutečnosti může být ve stavu "napadenému", ve kterém jeho kontext dočasně změnit.</span><span class="sxs-lookup"><span data-stu-id="7bf20-111">The debugger should call this method rather than the Win32 `SetThreadContext` function, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="7bf20-112">Tato metoda by měla používá, pokud se vlákna v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="7bf20-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="7bf20-113">Použití [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) pro vlákna ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="7bf20-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span> <span data-ttu-id="7bf20-114">Nikdy by měl budete muset upravit kontextu vlákno během ladění událost out-of-band (OOB).</span><span class="sxs-lookup"><span data-stu-id="7bf20-114">You should never need to modify the context of a thread during an out-of-band (OOB) debug event.</span></span>  
  
 <span data-ttu-id="7bf20-115">Data předaná musí být kontextu strukturu pro aktuální platformě.</span><span class="sxs-lookup"><span data-stu-id="7bf20-115">The data passed must be a context structure for the current platform.</span></span>  
  
 <span data-ttu-id="7bf20-116">Tato metoda může poškodit modul runtime, pokud používá nesprávně.</span><span class="sxs-lookup"><span data-stu-id="7bf20-116">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bf20-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7bf20-117">Requirements</span></span>  
 <span data-ttu-id="7bf20-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bf20-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bf20-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7bf20-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7bf20-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7bf20-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bf20-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bf20-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
