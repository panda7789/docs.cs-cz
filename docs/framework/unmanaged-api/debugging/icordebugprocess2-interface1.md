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
ms.openlocfilehash: 1ef6af11851acbe0f7e9469c9432ff09f9228608
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792509"
---
# <a name="icordebugprocess2-interface"></a><span data-ttu-id="5748d-102">ICorDebugProcess2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5748d-102">ICorDebugProcess2 Interface</span></span>
<span data-ttu-id="5748d-103">Logické rozšíření rozhraní ICorDebugProcess, které představuje proces spouštějící spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="5748d-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5748d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5748d-104">Methods</span></span>  
  
|<span data-ttu-id="5748d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5748d-105">Method</span></span>|<span data-ttu-id="5748d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5748d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5748d-107">ClearUnmanagedBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="5748d-107">ClearUnmanagedBreakpoint Method</span></span>](icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="5748d-108">Odstraní zarážku na zadaném posunu, který byl nastaven dřívějším voláním `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="5748d-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="5748d-109">GetDesiredNGENCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="5748d-109">GetDesiredNGENCompilerFlags Method</span></span>](icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="5748d-110">Získá příznaky, které musí být nastaveny pro modul CLR (Common Language Runtime) pro načtení obrázku do procesu, na který odkazuje tento `ICorDebugProcess2`.</span><span class="sxs-lookup"><span data-stu-id="5748d-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="5748d-111">GetReferenceValueFromGCHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="5748d-111">GetReferenceValueFromGCHandle Method</span></span>](icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="5748d-112">Získá ukazatel odkazu na zadaný spravovaný objekt, který má popisovač uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="5748d-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="5748d-113">GetThreadForTaskID – metoda</span><span class="sxs-lookup"><span data-stu-id="5748d-113">GetThreadForTaskID Method</span></span>](icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="5748d-114">Získá vlákno, na kterém je spuštěn úkol se zadaným identifikátorem.</span><span class="sxs-lookup"><span data-stu-id="5748d-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="5748d-115">GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="5748d-115">GetVersion Method</span></span>](icordebugprocess2-getversion-method.md)|<span data-ttu-id="5748d-116">Získá verzi modulu CLR, na které je spuštěn proces ladění.</span><span class="sxs-lookup"><span data-stu-id="5748d-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="5748d-117">SetDesiredNGENCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="5748d-117">SetDesiredNGENCompilerFlags Method</span></span>](icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="5748d-118">Nastaví příznaky, které jsou požadovány pro kompilátor JIT (just-in-time) k načtení obrázku do laděného procesu.</span><span class="sxs-lookup"><span data-stu-id="5748d-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="5748d-119">SetUnmanagedBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="5748d-119">SetUnmanagedBreakpoint Method</span></span>](icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="5748d-120">Nastaví nespravovanou zarážku na zadaném posunu nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="5748d-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5748d-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5748d-121">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5748d-122">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="5748d-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5748d-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5748d-123">Requirements</span></span>  
 <span data-ttu-id="5748d-124">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5748d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5748d-125">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5748d-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5748d-126">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5748d-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5748d-127">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5748d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5748d-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5748d-128">See also</span></span>

- [<span data-ttu-id="5748d-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="5748d-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
