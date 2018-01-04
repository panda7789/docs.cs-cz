---
title: "ICorDebugProcess::GetThreadContext – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e45d101db946747463ba4200bc5dd3b95d21391
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessgetthreadcontext-method"></a><span data-ttu-id="78cbe-102">ICorDebugProcess::GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="78cbe-102">ICorDebugProcess::GetThreadContext Method</span></span>
<span data-ttu-id="78cbe-103">Získá kontext pro dané vlákno v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="78cbe-103">Gets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78cbe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78cbe-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78cbe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78cbe-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="78cbe-106">[v] ID vlákna, pro které k načtení kontextu.</span><span class="sxs-lookup"><span data-stu-id="78cbe-106">[in] The ID of the thread for which to retrieve the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="78cbe-107">[v] Velikost `context` pole.</span><span class="sxs-lookup"><span data-stu-id="78cbe-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="78cbe-108">[ve out] Pole bajtů, které popisují obsah podprocesu.</span><span class="sxs-lookup"><span data-stu-id="78cbe-108">[in, out] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="78cbe-109">Kontext určuje architekturu procesoru, na kterém je prováděna vlákno.</span><span class="sxs-lookup"><span data-stu-id="78cbe-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78cbe-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="78cbe-110">Remarks</span></span>  
 <span data-ttu-id="78cbe-111">Ladicí program by měly volat tuto metodu, nikoli Win32 `GetThreadContext` metoda, protože vlákno ve skutečnosti může být ve stavu "napadenému", ve kterém jeho kontext dočasně změnit.</span><span class="sxs-lookup"><span data-stu-id="78cbe-111">The debugger should call this method rather than the Win32 `GetThreadContext` method, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="78cbe-112">Tato metoda by měla používá, pokud se vlákna v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="78cbe-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="78cbe-113">Použití [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) pro vlákna ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="78cbe-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span>  
  
 <span data-ttu-id="78cbe-114">S daty vrácenými je struktura kontext pro aktuální platformě.</span><span class="sxs-lookup"><span data-stu-id="78cbe-114">The data returned is a context structure for the current platform.</span></span> <span data-ttu-id="78cbe-115">Stejně jako v Win32 `GetThreadContext` metoda, měli byste inicializovat volající `context` parametr před voláním této metody.</span><span class="sxs-lookup"><span data-stu-id="78cbe-115">Just as with the Win32 `GetThreadContext` method, the caller should initialize the `context` parameter before calling this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78cbe-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78cbe-116">Requirements</span></span>  
 <span data-ttu-id="78cbe-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78cbe-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78cbe-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78cbe-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78cbe-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78cbe-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78cbe-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78cbe-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
