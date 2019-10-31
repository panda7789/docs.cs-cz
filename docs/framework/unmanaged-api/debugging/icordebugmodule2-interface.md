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
ms.openlocfilehash: a3a1b658f4ab05c7029de907882fe5ab2513ccd8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127887"
---
# <a name="icordebugmodule2-interface"></a><span data-ttu-id="0ac51-102">ICorDebugModule2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ac51-102">ICorDebugModule2 Interface</span></span>

<span data-ttu-id="0ac51-103">Slouží jako logické rozšíření rozhraní ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="0ac51-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0ac51-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0ac51-104">Methods</span></span>  
  
|<span data-ttu-id="0ac51-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0ac51-105">Method</span></span>|<span data-ttu-id="0ac51-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0ac51-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0ac51-107">ApplyChanges – metoda</span><span class="sxs-lookup"><span data-stu-id="0ac51-107">ApplyChanges Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|<span data-ttu-id="0ac51-108">Aplikuje změny v metadatech a změny v kódu jazyka MSIL (Microsoft Intermediate Language) na běžící proces.</span><span class="sxs-lookup"><span data-stu-id="0ac51-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="0ac51-109">GetJITCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="0ac51-109">GetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="0ac51-110">Získá příznaky, které řídí kompilaci JIT (just-in-time) pro tento `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="0ac51-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="0ac51-111">ResolveAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="0ac51-111">ResolveAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="0ac51-112">Přeloží sestavení, na které odkazuje zadaný token metadat.</span><span class="sxs-lookup"><span data-stu-id="0ac51-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="0ac51-113">SetJITCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="0ac51-113">SetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="0ac51-114">Nastaví příznaky, které řídí kompilaci JIT pro tento `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="0ac51-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="0ac51-115">SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="0ac51-115">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="0ac51-116">Nastaví Pouze můj kód (JMC) pro všechny metody všech tříd v tomto `ICorDebugModule2` na zadanou hodnotu, s výjimkou těch v poli `pTokens`, které se nastaví na opačnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0ac51-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ac51-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ac51-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ac51-118">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="0ac51-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ac51-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ac51-119">Requirements</span></span>  
 <span data-ttu-id="0ac51-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ac51-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ac51-121">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0ac51-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ac51-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0ac51-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ac51-123">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ac51-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ac51-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ac51-124">See also</span></span>

- [<span data-ttu-id="0ac51-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0ac51-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
