---
title: "Icordebugprocess2 – Interface1"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 80f6c35ba2ef2ec74293d0f025ddf20254f504a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess2-interface1"></a><span data-ttu-id="2d988-102">Icordebugprocess2 – Interface1</span><span class="sxs-lookup"><span data-stu-id="2d988-102">ICorDebugProcess2 Interface1</span></span>
<span data-ttu-id="2d988-103">Logické rozšíření ICorDebugProcess rozhraní, která představuje proces spuštěním spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="2d988-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2d988-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2d988-104">Methods</span></span>  
  
|<span data-ttu-id="2d988-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2d988-105">Method</span></span>|<span data-ttu-id="2d988-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2d988-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2d988-107">ClearUnmanagedBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="2d988-107">ClearUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="2d988-108">Odebere zarážek na zadaném posunu nastavený starší voláním `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="2d988-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="2d988-109">GetDesiredNGENCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="2d988-109">GetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="2d988-110">Získá příznaky, které musejí být nastaveny pro modul CLR (CLR) a načte bitovou kopii do procesu odkazuje toto `ICorDebugProcess2`.</span><span class="sxs-lookup"><span data-stu-id="2d988-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="2d988-111">GetReferenceValueFromGCHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="2d988-111">GetReferenceValueFromGCHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="2d988-112">Získá odkaz na ukazatel na zadaný spravovaný objekt, který je uvolnění paměti zpracovat.</span><span class="sxs-lookup"><span data-stu-id="2d988-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="2d988-113">GetThreadForTaskID – metoda</span><span class="sxs-lookup"><span data-stu-id="2d988-113">GetThreadForTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="2d988-114">Získá vláken, na kterém je prováděna úloha se zadaným identifikátorem.</span><span class="sxs-lookup"><span data-stu-id="2d988-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="2d988-115">GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="2d988-115">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|<span data-ttu-id="2d988-116">Získá verzi modulu CLR, na kterém je spuštěn proces laděné.</span><span class="sxs-lookup"><span data-stu-id="2d988-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="2d988-117">SetDesiredNGENCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="2d988-117">SetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="2d988-118">Nastaví příznaky, které jsou požadovány pro kompilátor za běhu (JIT) a načte bitovou kopii do procesu laděné.</span><span class="sxs-lookup"><span data-stu-id="2d988-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="2d988-119">SetUnmanagedBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="2d988-119">SetUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="2d988-120">Nastaví nespravované zarážek na posunu zadaný nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="2d988-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d988-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d988-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d988-122">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="2d988-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d988-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2d988-123">Requirements</span></span>  
 <span data-ttu-id="2d988-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d988-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d988-125">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d988-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d988-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d988-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d988-127">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d988-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d988-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d988-128">See Also</span></span>  
 [<span data-ttu-id="2d988-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2d988-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
