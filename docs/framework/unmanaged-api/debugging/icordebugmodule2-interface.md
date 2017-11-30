---
title: ICorDebugModule2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule2
helpviewer_keywords: ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 97259783d34babe3f0f229f5d62b3e945c0ac624
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodule2-interface1"></a><span data-ttu-id="748bc-102">ICorDebugModule2 Interface1</span><span class="sxs-lookup"><span data-stu-id="748bc-102">ICorDebugModule2 Interface1</span></span>
<span data-ttu-id="748bc-103">Slouží jako logické rozšíření rozhraní ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="748bc-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="748bc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="748bc-104">Methods</span></span>  
  
|<span data-ttu-id="748bc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="748bc-105">Method</span></span>|<span data-ttu-id="748bc-106">Popis</span><span class="sxs-lookup"><span data-stu-id="748bc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="748bc-107">ApplyChanges – metoda</span><span class="sxs-lookup"><span data-stu-id="748bc-107">ApplyChanges Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|<span data-ttu-id="748bc-108">Změny v metadatech a změny v kódu Microsoft (MSIL intermediate language) se vztahuje na běžící proces.</span><span class="sxs-lookup"><span data-stu-id="748bc-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="748bc-109">Getjitcompilerflags – metoda</span><span class="sxs-lookup"><span data-stu-id="748bc-109">GetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="748bc-110">Získá příznaky, které řídí kompilace v běhu (JIT) pro tento `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="748bc-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="748bc-111">Resolveassembly – metoda</span><span class="sxs-lookup"><span data-stu-id="748bc-111">ResolveAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="748bc-112">Přeloží sestavení odkazuje token Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="748bc-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="748bc-113">Setjitcompilerflags – metoda</span><span class="sxs-lookup"><span data-stu-id="748bc-113">SetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="748bc-114">Nastaví příznaky, které řídí JIT kompilace `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="748bc-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="748bc-115">Setjmcstatus – metoda</span><span class="sxs-lookup"><span data-stu-id="748bc-115">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="748bc-116">Nastaví stav pouze můj kód (SVK) ze všech metod všechny třídy v tomto `ICorDebugModule2` se zadanou hodnotou, s výjimkou těch, `pTokens` pole, které se nastaví na opačné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="748bc-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="748bc-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="748bc-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="748bc-118">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="748bc-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="748bc-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="748bc-119">Requirements</span></span>  
 <span data-ttu-id="748bc-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="748bc-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="748bc-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="748bc-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="748bc-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="748bc-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="748bc-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="748bc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="748bc-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="748bc-124">See Also</span></span>  
 [<span data-ttu-id="748bc-125">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="748bc-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
