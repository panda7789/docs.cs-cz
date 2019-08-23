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
ms.openlocfilehash: d8fe1a25c4bc1f5e19f49f0d660d0aad5a180ea2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911892"
---
# <a name="icordebugmodule2-interface"></a><span data-ttu-id="2135c-102">ICorDebugModule2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2135c-102">ICorDebugModule2 Interface</span></span>

<span data-ttu-id="2135c-103">Slouží jako logické rozšíření rozhraní ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="2135c-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2135c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2135c-104">Methods</span></span>  
  
|<span data-ttu-id="2135c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2135c-105">Method</span></span>|<span data-ttu-id="2135c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2135c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2135c-107">ApplyChanges – metoda</span><span class="sxs-lookup"><span data-stu-id="2135c-107">ApplyChanges Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|<span data-ttu-id="2135c-108">Aplikuje změny v metadatech a změny v kódu jazyka MSIL (Microsoft Intermediate Language) na běžící proces.</span><span class="sxs-lookup"><span data-stu-id="2135c-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="2135c-109">GetJITCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="2135c-109">GetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="2135c-110">Získá příznaky, které řídí kompilaci JIT (just-in-time) pro toto `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="2135c-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="2135c-111">ResolveAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="2135c-111">ResolveAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="2135c-112">Přeloží sestavení, na které odkazuje zadaný token metadat.</span><span class="sxs-lookup"><span data-stu-id="2135c-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="2135c-113">SetJITCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="2135c-113">SetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="2135c-114">Nastaví příznaky, které řídí kompilaci `ICorDebugModule2`JIT.</span><span class="sxs-lookup"><span data-stu-id="2135c-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="2135c-115">SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="2135c-115">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="2135c-116">Nastaví pouze můj kód (JMC) pro všechny metody všech tříd v této `ICorDebugModule2` třídě na zadanou hodnotu, s výjimkou těch `pTokens` v poli, které nastaví na opačnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2135c-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2135c-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2135c-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2135c-118">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="2135c-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2135c-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2135c-119">Requirements</span></span>  
 <span data-ttu-id="2135c-120">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2135c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2135c-121">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2135c-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2135c-122">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2135c-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2135c-123">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2135c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2135c-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2135c-124">See also</span></span>

- [<span data-ttu-id="2135c-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2135c-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
