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
ms.openlocfilehash: 3c57021061c1566b369cdd43847e3994cf54e2da
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139671"
---
# <a name="icordebugprocesssetthreadcontext-method"></a><span data-ttu-id="beaae-102">ICorDebugProcess::SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="beaae-102">ICorDebugProcess::SetThreadContext Method</span></span>
<span data-ttu-id="beaae-103">Nastaví kontext pro dané vlákno v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="beaae-103">Sets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beaae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="beaae-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="beaae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="beaae-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="beaae-106">pro ID vlákna, pro které chcete nastavit kontext.</span><span class="sxs-lookup"><span data-stu-id="beaae-106">[in] The ID of the thread for which to set the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="beaae-107">pro Velikost pole `context`.</span><span class="sxs-lookup"><span data-stu-id="beaae-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="beaae-108">pro Pole bajtů, které popisují kontext vlákna.</span><span class="sxs-lookup"><span data-stu-id="beaae-108">[in] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="beaae-109">Kontext určuje architekturu procesoru, ve kterém je vlákno spuštěno.</span><span class="sxs-lookup"><span data-stu-id="beaae-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="beaae-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="beaae-110">Remarks</span></span>  
 <span data-ttu-id="beaae-111">Ladicí program by měl volat tuto metodu namísto funkce Win32 `SetThreadContext`, protože vlákno může být ve skutečnosti ve stavu "napadeno", ve kterém byl jeho kontext dočasně změněn.</span><span class="sxs-lookup"><span data-stu-id="beaae-111">The debugger should call this method rather than the Win32 `SetThreadContext` function, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="beaae-112">Tato metoda by měla být použita pouze v případě, že vlákno je v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="beaae-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="beaae-113">Použijte [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) pro vlákna ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="beaae-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span> <span data-ttu-id="beaae-114">Nikdy byste neměli muset změnit kontext vlákna během události ladění OOB (out-of-band).</span><span class="sxs-lookup"><span data-stu-id="beaae-114">You should never need to modify the context of a thread during an out-of-band (OOB) debug event.</span></span>  
  
 <span data-ttu-id="beaae-115">Předaná data musí být kontextové struktury pro aktuální platformu.</span><span class="sxs-lookup"><span data-stu-id="beaae-115">The data passed must be a context structure for the current platform.</span></span>  
  
 <span data-ttu-id="beaae-116">Tato metoda může poškodit modul runtime, pokud je použit nesprávně.</span><span class="sxs-lookup"><span data-stu-id="beaae-116">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="beaae-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="beaae-117">Requirements</span></span>  
 <span data-ttu-id="beaae-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="beaae-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="beaae-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="beaae-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="beaae-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="beaae-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="beaae-121">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="beaae-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
