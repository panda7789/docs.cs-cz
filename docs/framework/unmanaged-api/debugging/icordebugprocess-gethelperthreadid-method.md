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
ms.openlocfilehash: fc4f4b56552c4db265d2ea123a84c7792ad53094
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213631"
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="f88c2-102">ICorDebugProcess::GetHelperThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="f88c2-102">ICorDebugProcess::GetHelperThreadID Method</span></span>
<span data-ttu-id="f88c2-103">Získá ID vlákna operačního systému (OS) vnitřního pomocného vlákna ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="f88c2-103">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f88c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f88c2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f88c2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f88c2-105">Parameters</span></span>  
 `pThreadID`  
 <span data-ttu-id="f88c2-106">mimo Ukazatel na ID vlákna operačního systému interní pomocné vlákno ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="f88c2-106">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f88c2-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f88c2-107">Remarks</span></span>  
 <span data-ttu-id="f88c2-108">Během spravovaného a nespravovaného ladění se jedná o zodpovědnost ladicího programu, aby se zajistilo, že vlákno se zadaným ID zůstává spuštěné, pokud narazí na zarážku umístěnou ladicím programem.</span><span class="sxs-lookup"><span data-stu-id="f88c2-108">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="f88c2-109">Ladicí program může také skrýt toto vlákno od uživatele.</span><span class="sxs-lookup"><span data-stu-id="f88c2-109">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="f88c2-110">Pokud v procesu ještě neexistuje žádné pomocné vlákno, `GetHelperThreadID` Metoda vrátí nulu v \* `pThreadID` .</span><span class="sxs-lookup"><span data-stu-id="f88c2-110">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in \*`pThreadID`.</span></span>  
  
 <span data-ttu-id="f88c2-111">Nemůžete ukládat do mezipaměti ID vlákna pomocných vláken, protože se může v průběhu času měnit.</span><span class="sxs-lookup"><span data-stu-id="f88c2-111">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="f88c2-112">Při každé události zastavení musíte znovu zadat dotaz na ID vlákna.</span><span class="sxs-lookup"><span data-stu-id="f88c2-112">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="f88c2-113">ID vlákna pomocného vlákna ladicího programu bude v každé nespravované události [ICorDebugManagedCallback:: CreateThread](icordebugmanagedcallback-createthread-method.md) správné, což umožňuje ladicímu programu určit ID vlákna jeho pomocného vlákna a skrýt ho od uživatele.</span><span class="sxs-lookup"><span data-stu-id="f88c2-113">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="f88c2-114">Vlákno, které je identifikováno jako pomocné vlákno během nespravované `ICorDebugManagedCallback::CreateThread` události, nikdy nespustí spravovaný kód uživatele.</span><span class="sxs-lookup"><span data-stu-id="f88c2-114">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f88c2-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f88c2-115">Requirements</span></span>  
 <span data-ttu-id="f88c2-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f88c2-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f88c2-117">**Hlavička:** CorDebug. idl.</span><span class="sxs-lookup"><span data-stu-id="f88c2-117">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="f88c2-118">CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f88c2-118">CorDebug.h</span></span>  
  
 <span data-ttu-id="f88c2-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f88c2-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f88c2-120">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f88c2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
