---
title: ICorDebugModule2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 192f2476aff91d3a8302d070852ab2a3722d137c
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970126"
---
# <a name="icordebugmodule2-interface"></a><span data-ttu-id="e6d68-102">ICorDebugModule2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e6d68-102">ICorDebugModule2 Interface</span></span>

<span data-ttu-id="e6d68-103">Slouží jako logické rozšíření pro icordebugmodule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e6d68-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e6d68-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e6d68-104">Methods</span></span>  
  
|<span data-ttu-id="e6d68-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e6d68-105">Method</span></span>|<span data-ttu-id="e6d68-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e6d68-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e6d68-107">ApplyChanges – metoda</span><span class="sxs-lookup"><span data-stu-id="e6d68-107">ApplyChanges Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|<span data-ttu-id="e6d68-108">Změny v metadatech a změny v kódu Microsoft intermediate language (MSIL) se vztahuje na běžící proces.</span><span class="sxs-lookup"><span data-stu-id="e6d68-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="e6d68-109">GetJITCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="e6d68-109">GetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="e6d68-110">Získá příznaky, které řídí kompilace just-in-time (JIT) pro tuto `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="e6d68-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="e6d68-111">ResolveAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="e6d68-111">ResolveAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="e6d68-112">Přeloží sestavení odkazuje token Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="e6d68-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="e6d68-113">SetJITCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="e6d68-113">SetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="e6d68-114">Nastaví příznaky, které řídí JIT kompilace `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="e6d68-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="e6d68-115">SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="e6d68-115">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="e6d68-116">Nastaví stav pouze můj kód (JMC) všech metod všechny třídy v tomto `ICorDebugModule2` se zadanou hodnotou, s výjimkou těch, `pTokens` pole, které se nastaví na opačnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e6d68-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6d68-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e6d68-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6d68-118">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="e6d68-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6d68-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e6d68-119">Requirements</span></span>  
 <span data-ttu-id="e6d68-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6d68-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6d68-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e6d68-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6d68-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6d68-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6d68-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6d68-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6d68-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6d68-124">See also</span></span>
- [<span data-ttu-id="e6d68-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e6d68-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
