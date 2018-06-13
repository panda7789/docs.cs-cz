---
title: ICorDebugModule2 Interface1
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
ms.openlocfilehash: 537023cf117477b54117799fc9ea62e894bb6591
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419137"
---
# <a name="icordebugmodule2-interface1"></a><span data-ttu-id="d53dd-102">ICorDebugModule2 Interface1</span><span class="sxs-lookup"><span data-stu-id="d53dd-102">ICorDebugModule2 Interface1</span></span>
<span data-ttu-id="d53dd-103">Slouží jako logické rozšíření rozhraní ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="d53dd-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d53dd-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d53dd-104">Methods</span></span>  
  
|<span data-ttu-id="d53dd-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d53dd-105">Method</span></span>|<span data-ttu-id="d53dd-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d53dd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d53dd-107">ApplyChanges – metoda</span><span class="sxs-lookup"><span data-stu-id="d53dd-107">ApplyChanges Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|<span data-ttu-id="d53dd-108">Změny v metadatech a změny v kódu Microsoft (MSIL intermediate language) se vztahuje na běžící proces.</span><span class="sxs-lookup"><span data-stu-id="d53dd-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="d53dd-109">GetJITCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="d53dd-109">GetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="d53dd-110">Získá příznaky, které řídí kompilace v běhu (JIT) pro tento `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="d53dd-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="d53dd-111">ResolveAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="d53dd-111">ResolveAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="d53dd-112">Přeloží sestavení odkazuje token Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="d53dd-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="d53dd-113">SetJITCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="d53dd-113">SetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="d53dd-114">Nastaví příznaky, které řídí JIT kompilace `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="d53dd-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="d53dd-115">SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="d53dd-115">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="d53dd-116">Nastaví stav pouze můj kód (SVK) ze všech metod všechny třídy v tomto `ICorDebugModule2` se zadanou hodnotou, s výjimkou těch, `pTokens` pole, které se nastaví na opačné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d53dd-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d53dd-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d53dd-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d53dd-118">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="d53dd-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d53dd-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d53dd-119">Requirements</span></span>  
 <span data-ttu-id="d53dd-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d53dd-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d53dd-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d53dd-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d53dd-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d53dd-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d53dd-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d53dd-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d53dd-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="d53dd-124">See Also</span></span>  
 [<span data-ttu-id="d53dd-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d53dd-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
