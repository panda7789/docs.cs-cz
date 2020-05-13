---
title: ICorDebugProcess2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2
helpviewer_keywords:
- ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type:
- apiref
ms.openlocfilehash: 1a57b7ceb6da961fba1f0d6e8e0ba1aa88ca0541
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213488"
---
# <a name="icordebugprocess2-interface"></a><span data-ttu-id="1b1dd-102">ICorDebugProcess2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b1dd-102">ICorDebugProcess2 Interface</span></span>
<span data-ttu-id="1b1dd-103">Logické rozšíření rozhraní ICorDebugProcess, které představuje proces spouštějící spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="1b1dd-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1b1dd-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1b1dd-104">Methods</span></span>  
  
|<span data-ttu-id="1b1dd-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1b1dd-105">Method</span></span>|<span data-ttu-id="1b1dd-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1b1dd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1b1dd-107">ClearUnmanagedBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="1b1dd-107">ClearUnmanagedBreakpoint Method</span></span>](icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="1b1dd-108">Odstraní zarážku na zadaném posunu, který byl nastaven dřívějším voláním metody `ICorDebugProcess2::SetUnmanagedBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="1b1dd-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="1b1dd-109">GetDesiredNGENCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="1b1dd-109">GetDesiredNGENCompilerFlags Method</span></span>](icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="1b1dd-110">Získá příznaky, které musí být nastaveny pro modul CLR (Common Language Runtime) k načtení obrázku do procesu, na který odkazuje `ICorDebugProcess2` .</span><span class="sxs-lookup"><span data-stu-id="1b1dd-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="1b1dd-111">GetReferenceValueFromGCHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="1b1dd-111">GetReferenceValueFromGCHandle Method</span></span>](icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="1b1dd-112">Získá ukazatel odkazu na zadaný spravovaný objekt, který má popisovač uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="1b1dd-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="1b1dd-113">GetThreadForTaskID – metoda</span><span class="sxs-lookup"><span data-stu-id="1b1dd-113">GetThreadForTaskID Method</span></span>](icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="1b1dd-114">Získá vlákno, na kterém je spuštěn úkol se zadaným identifikátorem.</span><span class="sxs-lookup"><span data-stu-id="1b1dd-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="1b1dd-115">GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="1b1dd-115">GetVersion Method</span></span>](icordebugprocess2-getversion-method.md)|<span data-ttu-id="1b1dd-116">Získá verzi modulu CLR, na které je spuštěn proces ladění.</span><span class="sxs-lookup"><span data-stu-id="1b1dd-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="1b1dd-117">SetDesiredNGENCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="1b1dd-117">SetDesiredNGENCompilerFlags Method</span></span>](icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="1b1dd-118">Nastaví příznaky, které jsou požadovány pro kompilátor JIT (just-in-time) k načtení obrázku do laděného procesu.</span><span class="sxs-lookup"><span data-stu-id="1b1dd-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="1b1dd-119">SetUnmanagedBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="1b1dd-119">SetUnmanagedBreakpoint Method</span></span>](icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="1b1dd-120">Nastaví nespravovanou zarážku na zadaném posunu nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="1b1dd-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b1dd-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1b1dd-121">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1b1dd-122">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="1b1dd-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b1dd-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1b1dd-123">Requirements</span></span>  
 <span data-ttu-id="1b1dd-124">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b1dd-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b1dd-125">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1b1dd-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b1dd-126">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1b1dd-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b1dd-127">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b1dd-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b1dd-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b1dd-128">See also</span></span>

- [<span data-ttu-id="1b1dd-129">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b1dd-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
