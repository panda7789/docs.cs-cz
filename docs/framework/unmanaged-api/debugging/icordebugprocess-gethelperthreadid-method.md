---
title: ICorDebugProcess::GetHelperThreadID – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHelperThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type:
- apiref
ms.openlocfilehash: d38a59b23d47cbaf57dc21e121d56530a514d354
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128864"
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="ca7fd-102">ICorDebugProcess::GetHelperThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="ca7fd-102">ICorDebugProcess::GetHelperThreadID Method</span></span>
<span data-ttu-id="ca7fd-103">Získá ID vlákna operačního systému (OS) vnitřního pomocného vlákna ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="ca7fd-103">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca7fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca7fd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca7fd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ca7fd-105">Parameters</span></span>  
 `pThreadID`  
 <span data-ttu-id="ca7fd-106">mimo Ukazatel na ID vlákna operačního systému interní pomocné vlákno ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="ca7fd-106">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca7fd-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ca7fd-107">Remarks</span></span>  
 <span data-ttu-id="ca7fd-108">Během spravovaného a nespravovaného ladění se jedná o zodpovědnost ladicího programu, aby se zajistilo, že vlákno se zadaným ID zůstává spuštěné, pokud narazí na zarážku umístěnou ladicím programem.</span><span class="sxs-lookup"><span data-stu-id="ca7fd-108">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="ca7fd-109">Ladicí program může také skrýt toto vlákno od uživatele.</span><span class="sxs-lookup"><span data-stu-id="ca7fd-109">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="ca7fd-110">Pokud v procesu ještě neexistuje žádný pomocný podproces, metoda `GetHelperThreadID` vrátí nulu ve \*`pThreadID`.</span><span class="sxs-lookup"><span data-stu-id="ca7fd-110">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in \*`pThreadID`.</span></span>  
  
 <span data-ttu-id="ca7fd-111">Nemůžete ukládat do mezipaměti ID vlákna pomocných vláken, protože se může v průběhu času měnit.</span><span class="sxs-lookup"><span data-stu-id="ca7fd-111">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="ca7fd-112">Při každé události zastavení musíte znovu zadat dotaz na ID vlákna.</span><span class="sxs-lookup"><span data-stu-id="ca7fd-112">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="ca7fd-113">ID vlákna pomocného vlákna ladicího programu bude v každé nespravované události [ICorDebugManagedCallback:: CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) správné, což umožňuje ladicímu programu určit ID vlákna jeho pomocného vlákna a skrýt ho od uživatele.</span><span class="sxs-lookup"><span data-stu-id="ca7fd-113">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="ca7fd-114">Vlákno, které je identifikováno jako pomocné vlákno během nespravované události `ICorDebugManagedCallback::CreateThread`, nikdy nespustí spravovaný kód uživatele.</span><span class="sxs-lookup"><span data-stu-id="ca7fd-114">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca7fd-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ca7fd-115">Requirements</span></span>  
 <span data-ttu-id="ca7fd-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca7fd-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca7fd-117">**Hlavička:** CorDebug. idl.</span><span class="sxs-lookup"><span data-stu-id="ca7fd-117">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="ca7fd-118">CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ca7fd-118">CorDebug.h</span></span>  
  
 <span data-ttu-id="ca7fd-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ca7fd-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca7fd-120">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca7fd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
