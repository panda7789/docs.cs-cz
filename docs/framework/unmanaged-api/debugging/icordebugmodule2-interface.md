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
ms.openlocfilehash: 7b98302985d9d54599ea8ea2e01dc2503c468d58
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210225"
---
# <a name="icordebugmodule2-interface"></a><span data-ttu-id="89eda-102">ICorDebugModule2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89eda-102">ICorDebugModule2 Interface</span></span>

<span data-ttu-id="89eda-103">Slouží jako logické rozšíření rozhraní ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="89eda-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="89eda-104">Metody</span><span class="sxs-lookup"><span data-stu-id="89eda-104">Methods</span></span>  
  
|<span data-ttu-id="89eda-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="89eda-105">Method</span></span>|<span data-ttu-id="89eda-106">Popis</span><span class="sxs-lookup"><span data-stu-id="89eda-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="89eda-107">ApplyChanges – metoda</span><span class="sxs-lookup"><span data-stu-id="89eda-107">ApplyChanges Method</span></span>](icordebugmodule2-applychanges-method.md)|<span data-ttu-id="89eda-108">Aplikuje změny v metadatech a změny v kódu jazyka MSIL (Microsoft Intermediate Language) na běžící proces.</span><span class="sxs-lookup"><span data-stu-id="89eda-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="89eda-109">GetJITCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="89eda-109">GetJITCompilerFlags Method</span></span>](icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="89eda-110">Získá příznaky, které řídí kompilaci JIT (just-in-time) pro toto `ICorDebugModule2` .</span><span class="sxs-lookup"><span data-stu-id="89eda-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="89eda-111">ResolveAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="89eda-111">ResolveAssembly Method</span></span>](icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="89eda-112">Přeloží sestavení, na které odkazuje zadaný token metadat.</span><span class="sxs-lookup"><span data-stu-id="89eda-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="89eda-113">SetJITCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="89eda-113">SetJITCompilerFlags Method</span></span>](icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="89eda-114">Nastaví příznaky, které řídí kompilaci JIT `ICorDebugModule2` .</span><span class="sxs-lookup"><span data-stu-id="89eda-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="89eda-115">SetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="89eda-115">SetJMCStatus Method</span></span>](icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="89eda-116">Nastaví Pouze můj kód (JMC) pro všechny metody všech tříd v této třídě `ICorDebugModule2` na zadanou hodnotu, s výjimkou těch v `pTokens` poli, které nastaví na opačnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="89eda-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89eda-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89eda-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89eda-118">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="89eda-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89eda-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89eda-119">Requirements</span></span>  
 <span data-ttu-id="89eda-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89eda-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89eda-121">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="89eda-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89eda-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="89eda-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89eda-123">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89eda-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89eda-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="89eda-124">See also</span></span>

- [<span data-ttu-id="89eda-125">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89eda-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
