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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49b3bb51f307093ea1cc8cc45064d5c405974822
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178019"
---
# <a name="icordebugprocess2-interface"></a><span data-ttu-id="6f7d2-102">ICorDebugProcess2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f7d2-102">ICorDebugProcess2 Interface</span></span>
<span data-ttu-id="6f7d2-103">Logické rozšíření icordebugprocess – rozhraní, která představuje proces spuštění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="6f7d2-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6f7d2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6f7d2-104">Methods</span></span>  
  
|<span data-ttu-id="6f7d2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6f7d2-105">Method</span></span>|<span data-ttu-id="6f7d2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6f7d2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6f7d2-107">ClearUnmanagedBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="6f7d2-107">ClearUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="6f7d2-108">Odstraní zarážku v zadaném posunu, který nastavil dřívějším volání `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="6f7d2-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="6f7d2-109">GetDesiredNGENCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="6f7d2-109">GetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="6f7d2-110">Získá příznaky, které musí být nastavena pro modul common language runtime (CLR) pro načtení obrázku do procesu odkazovaná tímto objektem `ICorDebugProcess2`.</span><span class="sxs-lookup"><span data-stu-id="6f7d2-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="6f7d2-111">GetReferenceValueFromGCHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="6f7d2-111">GetReferenceValueFromGCHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="6f7d2-112">Získá odkaz na ukazatel na zadaný spravovaný objekt, který má uvolňování paměti zpracovávají.</span><span class="sxs-lookup"><span data-stu-id="6f7d2-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="6f7d2-113">GetThreadForTaskID – metoda</span><span class="sxs-lookup"><span data-stu-id="6f7d2-113">GetThreadForTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="6f7d2-114">Získá vlákno, na kterých je prováděna úloha se zadaným identifikátorem.</span><span class="sxs-lookup"><span data-stu-id="6f7d2-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="6f7d2-115">GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="6f7d2-115">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|<span data-ttu-id="6f7d2-116">Získá verzi CLR, na kterém je spuštěna laděného procesu.</span><span class="sxs-lookup"><span data-stu-id="6f7d2-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="6f7d2-117">SetDesiredNGENCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="6f7d2-117">SetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="6f7d2-118">Nastaví příznaky, které jsou požadovány pro kompilátor just-in-time (JIT) pro načtení obrázku do laděného procesu.</span><span class="sxs-lookup"><span data-stu-id="6f7d2-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="6f7d2-119">SetUnmanagedBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="6f7d2-119">SetUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="6f7d2-120">Nastaví nespravované zarážku posunem zadaným nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="6f7d2-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f7d2-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6f7d2-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f7d2-122">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="6f7d2-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f7d2-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f7d2-123">Requirements</span></span>  
 <span data-ttu-id="6f7d2-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f7d2-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f7d2-125">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f7d2-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f7d2-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f7d2-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f7d2-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f7d2-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f7d2-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6f7d2-128">See also</span></span>

- [<span data-ttu-id="6f7d2-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6f7d2-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
