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
ms.openlocfilehash: e01f94e9574ebc032bc45490fd88ff92e9104aa3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482857"
---
# <a name="icordebugthreadenumeratechains-method"></a><span data-ttu-id="ff4c4-102">ICorDebugThread::EnumerateChains – metoda</span><span class="sxs-lookup"><span data-stu-id="ff4c4-102">ICorDebugThread::EnumerateChains Method</span></span>
<span data-ttu-id="ff4c4-103">Získá enumerátor icordebugchainenum –, který obsahuje všechny řetězů zásobníku v tomto objektu ICorDebugThread ukazatel rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ff4c4-103">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff4c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff4c4-104">Syntax</span></span>  
  
```  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff4c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff4c4-105">Parameters</span></span>  
 `ppChains`  
 <span data-ttu-id="ff4c4-106">[out] Ukazatel na adresu `ICorDebugChainEnum` zřetězí objekt, který umožňuje výčet všech zásobníku v tomto vláknu, začíná řetězec aktivní (to znamená, poslední).</span><span class="sxs-lookup"><span data-stu-id="ff4c4-106">[out] A pointer to the address of an `ICorDebugChainEnum` object that allows enumeration of all the stack chains in this thread, starting at the active (that is, the most recent) chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff4c4-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff4c4-107">Remarks</span></span>  
 <span data-ttu-id="ff4c4-108">Řetěz zásobníku představuje fyzické volání zásobníku pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="ff4c4-108">The stack chain represents the physical call stack for the thread.</span></span> <span data-ttu-id="ff4c4-109">V následujících případech vytvoření hranice řetěz zásobníku:</span><span class="sxs-lookup"><span data-stu-id="ff4c4-109">The following circumstances create a stack chain boundary:</span></span>  
  
-   <span data-ttu-id="ff4c4-110">Spravované na nespravované nebo nespravovaného do spravovaného přechodu.</span><span class="sxs-lookup"><span data-stu-id="ff4c4-110">A managed-to-unmanaged or unmanaged-to-managed transition.</span></span>  
  
-   <span data-ttu-id="ff4c4-111">Přepnutí kontextu.</span><span class="sxs-lookup"><span data-stu-id="ff4c4-111">A context switch.</span></span>  
  
-   <span data-ttu-id="ff4c4-112">A zneužití uživatelské vlákno ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="ff4c4-112">A debugger hijacking of a user thread.</span></span>  
  
 <span data-ttu-id="ff4c4-113">V jednoduchém případě pro vlákno, na kterém běží v rámci jednoho čistě spravovaném kódu bude existovat shoda mezi vlákny a řetězů zásobníku.</span><span class="sxs-lookup"><span data-stu-id="ff4c4-113">In the simple case for a thread that is running purely managed code in a single context, a one-to-one correspondence will exist between threads and stack chains.</span></span>  
  
 <span data-ttu-id="ff4c4-114">Ladicí program může být vhodné ke změně uspořádání zásobníky fyzická volání všech vláken v logické zásobníky volání.</span><span class="sxs-lookup"><span data-stu-id="ff4c4-114">A debugger may want to rearrange the physical call stacks of all threads into logical call stacks.</span></span> <span data-ttu-id="ff4c4-115">To by vyžadovalo řazení řetězců všechna vlákna podle jejich vztahů volající/volaný a přerozdělit je.</span><span class="sxs-lookup"><span data-stu-id="ff4c4-115">This would involve sorting all the threads' chains by their caller/callee relationships and regrouping them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff4c4-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff4c4-116">Requirements</span></span>  
 <span data-ttu-id="ff4c4-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff4c4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff4c4-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff4c4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff4c4-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff4c4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff4c4-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff4c4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
