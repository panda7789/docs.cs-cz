---
title: ICorDebugProcess::GetThreadContext – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28d54becc2d7cd4359c78415f25f579b968cb3f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775596"
---
# <a name="icordebugprocessgetthreadcontext-method"></a><span data-ttu-id="8a907-102">ICorDebugProcess::GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="8a907-102">ICorDebugProcess::GetThreadContext Method</span></span>
<span data-ttu-id="8a907-103">Získá kontext pro dané vlákno v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="8a907-103">Gets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a907-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a907-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a907-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a907-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="8a907-106">[in] ID vlákna, pro které se mají načíst kontext.</span><span class="sxs-lookup"><span data-stu-id="8a907-106">[in] The ID of the thread for which to retrieve the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="8a907-107">[in] Velikost `context` pole.</span><span class="sxs-lookup"><span data-stu-id="8a907-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="8a907-108">[out v] Pole bajtů, které popisují kontext vlákna.</span><span class="sxs-lookup"><span data-stu-id="8a907-108">[in, out] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="8a907-109">Kontext určuje architekturu procesoru, na kterém vlákno prováděno.</span><span class="sxs-lookup"><span data-stu-id="8a907-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a907-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8a907-110">Remarks</span></span>  
 <span data-ttu-id="8a907-111">Ladicí program by měly volat tuto metodu, spíše než Win32 `GetThreadContext` metody, protože vlákno může být ve skutečnosti ve stavu "napadenému", ve kterém jeho kontext dočasně změnit.</span><span class="sxs-lookup"><span data-stu-id="8a907-111">The debugger should call this method rather than the Win32 `GetThreadContext` method, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="8a907-112">Tato metoda by měla sloužit pouze v případě vlákna v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="8a907-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="8a907-113">Použití [icordebugregisterset –](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) pro vlákna ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="8a907-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span>  
  
 <span data-ttu-id="8a907-114">Data vrácená je struktura kontext pro aktuální platformu.</span><span class="sxs-lookup"><span data-stu-id="8a907-114">The data returned is a context structure for the current platform.</span></span> <span data-ttu-id="8a907-115">Stejně jako u Win32 `GetThreadContext` metodu, volající by měl inicializovat `context` parametr před voláním této metody.</span><span class="sxs-lookup"><span data-stu-id="8a907-115">Just as with the Win32 `GetThreadContext` method, the caller should initialize the `context` parameter before calling this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a907-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8a907-116">Requirements</span></span>  
 <span data-ttu-id="8a907-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a907-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a907-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a907-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a907-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a907-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a907-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a907-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
