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
ms.openlocfilehash: 5519714ff2b4ee67d0e59001bf5b454cdc25d648
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961083"
---
# <a name="icordebugprocess2-interface"></a><span data-ttu-id="bafbb-102">ICorDebugProcess2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bafbb-102">ICorDebugProcess2 Interface</span></span>
<span data-ttu-id="bafbb-103">Logické rozšíření rozhraní ICorDebugProcess, které představuje proces spouštějící spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="bafbb-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bafbb-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bafbb-104">Methods</span></span>  
  
|<span data-ttu-id="bafbb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bafbb-105">Method</span></span>|<span data-ttu-id="bafbb-106">Popis</span><span class="sxs-lookup"><span data-stu-id="bafbb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bafbb-107">ClearUnmanagedBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="bafbb-107">ClearUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="bafbb-108">Odstraní zarážku na zadaném posunu, který byl nastaven dřívějším voláním `ICorDebugProcess2::SetUnmanagedBreakpoint`metody.</span><span class="sxs-lookup"><span data-stu-id="bafbb-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="bafbb-109">GetDesiredNGENCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="bafbb-109">GetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="bafbb-110">Získá příznaky, které musí být nastaveny pro modul CLR (Common Language Runtime) k načtení obrázku do procesu, na který odkazuje `ICorDebugProcess2`.</span><span class="sxs-lookup"><span data-stu-id="bafbb-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="bafbb-111">GetReferenceValueFromGCHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="bafbb-111">GetReferenceValueFromGCHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="bafbb-112">Získá ukazatel odkazu na zadaný spravovaný objekt, který má popisovač uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="bafbb-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="bafbb-113">GetThreadForTaskID – metoda</span><span class="sxs-lookup"><span data-stu-id="bafbb-113">GetThreadForTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="bafbb-114">Získá vlákno, na kterém je spuštěn úkol se zadaným identifikátorem.</span><span class="sxs-lookup"><span data-stu-id="bafbb-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="bafbb-115">GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="bafbb-115">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|<span data-ttu-id="bafbb-116">Získá verzi modulu CLR, na které je spuštěn proces ladění.</span><span class="sxs-lookup"><span data-stu-id="bafbb-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="bafbb-117">SetDesiredNGENCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="bafbb-117">SetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="bafbb-118">Nastaví příznaky, které jsou požadovány pro kompilátor JIT (just-in-time) k načtení obrázku do laděného procesu.</span><span class="sxs-lookup"><span data-stu-id="bafbb-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="bafbb-119">SetUnmanagedBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="bafbb-119">SetUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="bafbb-120">Nastaví nespravovanou zarážku na zadaném posunu nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="bafbb-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bafbb-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bafbb-121">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bafbb-122">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="bafbb-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bafbb-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bafbb-123">Requirements</span></span>  
 <span data-ttu-id="bafbb-124">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bafbb-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bafbb-125">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bafbb-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bafbb-126">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bafbb-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bafbb-127">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bafbb-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bafbb-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bafbb-128">See also</span></span>

- [<span data-ttu-id="bafbb-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="bafbb-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
