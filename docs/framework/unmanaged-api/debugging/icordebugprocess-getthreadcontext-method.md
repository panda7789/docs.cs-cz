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
ms.openlocfilehash: 41c5116d23655730f3586dc656aa69c8ae817b6c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792627"
---
# <a name="icordebugprocessgetthreadcontext-method"></a><span data-ttu-id="575f4-102">ICorDebugProcess::GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="575f4-102">ICorDebugProcess::GetThreadContext Method</span></span>
<span data-ttu-id="575f4-103">Získá kontext pro dané vlákno v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="575f4-103">Gets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="575f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="575f4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="575f4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="575f4-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="575f4-106">pro ID vlákna, pro které má být načten kontext.</span><span class="sxs-lookup"><span data-stu-id="575f4-106">[in] The ID of the thread for which to retrieve the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="575f4-107">pro Velikost pole `context`.</span><span class="sxs-lookup"><span data-stu-id="575f4-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="575f4-108">[in, out] Pole bajtů, které popisují kontext vlákna.</span><span class="sxs-lookup"><span data-stu-id="575f4-108">[in, out] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="575f4-109">Kontext určuje architekturu procesoru, ve kterém je vlákno spuštěno.</span><span class="sxs-lookup"><span data-stu-id="575f4-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="575f4-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="575f4-110">Remarks</span></span>  
 <span data-ttu-id="575f4-111">Ladicí program by měl volat tuto metodu, spíše než Win32 `GetThreadContext` metoda, protože vlákno může být ve skutečnosti ve stavu "napadeno", ve kterém byl jeho kontext dočasně změněn.</span><span class="sxs-lookup"><span data-stu-id="575f4-111">The debugger should call this method rather than the Win32 `GetThreadContext` method, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="575f4-112">Tato metoda by měla být použita pouze v případě, že vlákno je v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="575f4-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="575f4-113">Použijte [ICorDebugRegisterSet](icordebugregisterset-interface.md) pro vlákna ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="575f4-113">Use [ICorDebugRegisterSet](icordebugregisterset-interface.md) for threads in managed code.</span></span>  
  
 <span data-ttu-id="575f4-114">Vrácená data jsou kontextovou strukturou pro aktuální platformu.</span><span class="sxs-lookup"><span data-stu-id="575f4-114">The data returned is a context structure for the current platform.</span></span> <span data-ttu-id="575f4-115">Stejně jako u metody Win32 `GetThreadContext` by volající měl inicializovat parametr `context` před voláním této metody.</span><span class="sxs-lookup"><span data-stu-id="575f4-115">Just as with the Win32 `GetThreadContext` method, the caller should initialize the `context` parameter before calling this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="575f4-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="575f4-116">Requirements</span></span>  
 <span data-ttu-id="575f4-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="575f4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="575f4-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="575f4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="575f4-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="575f4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="575f4-120">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="575f4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
