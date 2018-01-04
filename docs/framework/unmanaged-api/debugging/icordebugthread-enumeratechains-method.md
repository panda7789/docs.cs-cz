---
title: "ICorDebugThread::EnumerateChains – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.EnumerateChains
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e6a9637edb4a846b4d10dd6565533a9219ad558
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadenumeratechains-method"></a><span data-ttu-id="c4b86-102">ICorDebugThread::EnumerateChains – metoda</span><span class="sxs-lookup"><span data-stu-id="c4b86-102">ICorDebugThread::EnumerateChains Method</span></span>
<span data-ttu-id="c4b86-103">Získá ukazatele rozhraní na enumerátor ICorDebugChainEnum, který obsahuje všechny řetězy zásobníku v tomto objektu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="c4b86-103">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4b86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4b86-104">Syntax</span></span>  
  
```  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c4b86-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4b86-105">Parameters</span></span>  
 `ppChains`  
 <span data-ttu-id="c4b86-106">[out] Ukazatel na adresu `ICorDebugChainEnum` objekt, který umožňuje výčet všech zásobníku zřetězený v tohoto podprocesu počínaje řetězu aktivní (tedy nejnovější).</span><span class="sxs-lookup"><span data-stu-id="c4b86-106">[out] A pointer to the address of an `ICorDebugChainEnum` object that allows enumeration of all the stack chains in this thread, starting at the active (that is, the most recent) chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4b86-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4b86-107">Remarks</span></span>  
 <span data-ttu-id="c4b86-108">Řetězu zásobník představuje zásobníku volání fyzické pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="c4b86-108">The stack chain represents the physical call stack for the thread.</span></span> <span data-ttu-id="c4b86-109">V těchto případech vytvoření hranice řetězu zásobníku:</span><span class="sxs-lookup"><span data-stu-id="c4b86-109">The following circumstances create a stack chain boundary:</span></span>  
  
-   <span data-ttu-id="c4b86-110">Spravované na nespravované nebo nespravovaného do spravovaného přechod.</span><span class="sxs-lookup"><span data-stu-id="c4b86-110">A managed-to-unmanaged or unmanaged-to-managed transition.</span></span>  
  
-   <span data-ttu-id="c4b86-111">Kontext přepínač.</span><span class="sxs-lookup"><span data-stu-id="c4b86-111">A context switch.</span></span>  
  
-   <span data-ttu-id="c4b86-112">A zneužití uživatelské vlákno ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="c4b86-112">A debugger hijacking of a user thread.</span></span>  
  
 <span data-ttu-id="c4b86-113">V případě jednoduchého pro vlákno, které běží v kontextu jedné čistě spravovaného kódu, budou existovat souvislosti mezi vláken a řetězy zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c4b86-113">In the simple case for a thread that is running purely managed code in a single context, a one-to-one correspondence will exist between threads and stack chains.</span></span>  
  
 <span data-ttu-id="c4b86-114">Ladicí program chtít Změna uspořádání zásobníky volání fyzické všechny podprocesy do zásobníky logické volání.</span><span class="sxs-lookup"><span data-stu-id="c4b86-114">A debugger may want to rearrange the physical call stacks of all threads into logical call stacks.</span></span> <span data-ttu-id="c4b86-115">To by zahrnovat všechny vláken řetězy řazení podle jejich volající/volaný vztahů a přerozdělit je.</span><span class="sxs-lookup"><span data-stu-id="c4b86-115">This would involve sorting all the threads' chains by their caller/callee relationships and regrouping them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4b86-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4b86-116">Requirements</span></span>  
 <span data-ttu-id="c4b86-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4b86-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4b86-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4b86-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4b86-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4b86-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4b86-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4b86-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
