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
ms.openlocfilehash: d3fb1bf3f61c78f4eb157b93363b1c06b25bee04
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119896"
---
# <a name="icordebugmodule2-interface"></a><span data-ttu-id="1aed1-102">ICorDebugModule2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1aed1-102">ICorDebugModule2 Interface</span></span>

<span data-ttu-id="1aed1-103">Slouží jako logické rozšíření pro icordebugmodule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1aed1-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1aed1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1aed1-104">Methods</span></span>  
  
|<span data-ttu-id="1aed1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1aed1-105">Method</span></span>|<span data-ttu-id="1aed1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1aed1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1aed1-107">ApplyChanges – metoda</span><span class="sxs-lookup"><span data-stu-id="1aed1-107">ApplyChanges Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|<span data-ttu-id="1aed1-108">Změny v metadatech a změny v kódu Microsoft intermediate language (MSIL) se vztahuje na běžící proces.</span><span class="sxs-lookup"><span data-stu-id="1aed1-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="1aed1-109">GetJITCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="1aed1-109">GetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="1aed1-110">Získá příznaky, které řídí kompilace just-in-time (JIT) pro tuto `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="1aed1-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="1aed1-111">ResolveAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="1aed1-111">ResolveAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="1aed1-112">Přeloží sestavení odkazuje token Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="1aed1-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="1aed1-113">SetJITCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="1aed1-113">SetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="1aed1-114">Nastaví příznaky, které řídí JIT kompilace `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="1aed1-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="1aed1-115">SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="1aed1-115">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="1aed1-116">Nastaví stav pouze můj kód (JMC) všech metod všechny třídy v tomto `ICorDebugModule2` se zadanou hodnotou, s výjimkou těch, `pTokens` pole, které se nastaví na opačnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1aed1-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1aed1-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1aed1-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1aed1-118">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="1aed1-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1aed1-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1aed1-119">Requirements</span></span>  
 <span data-ttu-id="1aed1-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1aed1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1aed1-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1aed1-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1aed1-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1aed1-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1aed1-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1aed1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aed1-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1aed1-124">See also</span></span>

- [<span data-ttu-id="1aed1-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="1aed1-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
