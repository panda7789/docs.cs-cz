---
title: ICorDebugThread::EnumerateChains – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.EnumerateChains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6f0ed843f72d3f1e1575da15776a94a9097fd02
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771099"
---
# <a name="icordebugthreadenumeratechains-method"></a><span data-ttu-id="15f83-102">ICorDebugThread::EnumerateChains – metoda</span><span class="sxs-lookup"><span data-stu-id="15f83-102">ICorDebugThread::EnumerateChains Method</span></span>
<span data-ttu-id="15f83-103">Získá enumerátor icordebugchainenum –, který obsahuje všechny řetězů zásobníku v tomto objektu ICorDebugThread ukazatel rozhraní.</span><span class="sxs-lookup"><span data-stu-id="15f83-103">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15f83-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15f83-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15f83-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="15f83-105">Parameters</span></span>  
 `ppChains`  
 <span data-ttu-id="15f83-106">[out] Ukazatel na adresu `ICorDebugChainEnum` zřetězí objekt, který umožňuje výčet všech zásobníku v tomto vláknu, začíná řetězec aktivní (to znamená, poslední).</span><span class="sxs-lookup"><span data-stu-id="15f83-106">[out] A pointer to the address of an `ICorDebugChainEnum` object that allows enumeration of all the stack chains in this thread, starting at the active (that is, the most recent) chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15f83-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15f83-107">Remarks</span></span>  
 <span data-ttu-id="15f83-108">Řetěz zásobníku představuje fyzické volání zásobníku pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="15f83-108">The stack chain represents the physical call stack for the thread.</span></span> <span data-ttu-id="15f83-109">V následujících případech vytvoření hranice řetěz zásobníku:</span><span class="sxs-lookup"><span data-stu-id="15f83-109">The following circumstances create a stack chain boundary:</span></span>  
  
- <span data-ttu-id="15f83-110">Spravované na nespravované nebo nespravovaného do spravovaného přechodu.</span><span class="sxs-lookup"><span data-stu-id="15f83-110">A managed-to-unmanaged or unmanaged-to-managed transition.</span></span>  
  
- <span data-ttu-id="15f83-111">Přepnutí kontextu.</span><span class="sxs-lookup"><span data-stu-id="15f83-111">A context switch.</span></span>  
  
- <span data-ttu-id="15f83-112">A zneužití uživatelské vlákno ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="15f83-112">A debugger hijacking of a user thread.</span></span>  
  
 <span data-ttu-id="15f83-113">V jednoduchém případě pro vlákno, na kterém běží v rámci jednoho čistě spravovaném kódu bude existovat shoda mezi vlákny a řetězů zásobníku.</span><span class="sxs-lookup"><span data-stu-id="15f83-113">In the simple case for a thread that is running purely managed code in a single context, a one-to-one correspondence will exist between threads and stack chains.</span></span>  
  
 <span data-ttu-id="15f83-114">Ladicí program může být vhodné ke změně uspořádání zásobníky fyzická volání všech vláken v logické zásobníky volání.</span><span class="sxs-lookup"><span data-stu-id="15f83-114">A debugger may want to rearrange the physical call stacks of all threads into logical call stacks.</span></span> <span data-ttu-id="15f83-115">To by vyžadovalo řazení řetězců všechna vlákna podle jejich vztahů volající/volaný a přerozdělit je.</span><span class="sxs-lookup"><span data-stu-id="15f83-115">This would involve sorting all the threads' chains by their caller/callee relationships and regrouping them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15f83-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15f83-116">Requirements</span></span>  
 <span data-ttu-id="15f83-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15f83-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15f83-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="15f83-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15f83-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15f83-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15f83-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15f83-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
