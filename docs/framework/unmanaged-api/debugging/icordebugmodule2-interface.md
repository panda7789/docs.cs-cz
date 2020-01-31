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
ms.openlocfilehash: 32774aacecf3e56510bc6f0670538a44fde794c9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792989"
---
# <a name="icordebugmodule2-interface"></a><span data-ttu-id="59277-102">ICorDebugModule2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="59277-102">ICorDebugModule2 Interface</span></span>

<span data-ttu-id="59277-103">Slouží jako logické rozšíření rozhraní ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="59277-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59277-104">Metody</span><span class="sxs-lookup"><span data-stu-id="59277-104">Methods</span></span>  
  
|<span data-ttu-id="59277-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="59277-105">Method</span></span>|<span data-ttu-id="59277-106">Popis</span><span class="sxs-lookup"><span data-stu-id="59277-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59277-107">ApplyChanges – metoda</span><span class="sxs-lookup"><span data-stu-id="59277-107">ApplyChanges Method</span></span>](icordebugmodule2-applychanges-method.md)|<span data-ttu-id="59277-108">Aplikuje změny v metadatech a změny v kódu jazyka MSIL (Microsoft Intermediate Language) na běžící proces.</span><span class="sxs-lookup"><span data-stu-id="59277-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="59277-109">GetJITCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="59277-109">GetJITCompilerFlags Method</span></span>](icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="59277-110">Získá příznaky, které řídí kompilaci JIT (just-in-time) pro tento `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="59277-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="59277-111">ResolveAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="59277-111">ResolveAssembly Method</span></span>](icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="59277-112">Přeloží sestavení, na které odkazuje zadaný token metadat.</span><span class="sxs-lookup"><span data-stu-id="59277-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="59277-113">SetJITCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="59277-113">SetJITCompilerFlags Method</span></span>](icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="59277-114">Nastaví příznaky, které řídí kompilaci JIT pro tento `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="59277-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="59277-115">SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="59277-115">SetJMCStatus Method</span></span>](icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="59277-116">Nastaví Pouze můj kód (JMC) pro všechny metody všech tříd v tomto `ICorDebugModule2` na zadanou hodnotu, s výjimkou těch v poli `pTokens`, které se nastaví na opačnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="59277-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59277-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="59277-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="59277-118">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="59277-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59277-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="59277-119">Requirements</span></span>  
 <span data-ttu-id="59277-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59277-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59277-121">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="59277-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59277-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="59277-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59277-123">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59277-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59277-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59277-124">See also</span></span>

- [<span data-ttu-id="59277-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="59277-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
