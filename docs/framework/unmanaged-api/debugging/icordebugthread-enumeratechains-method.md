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
ms.openlocfilehash: 711fccd65379bc3e5e178869e7220dd84fd07fbe
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379706"
---
# <a name="icordebugthreadenumeratechains-method"></a><span data-ttu-id="b441c-102">ICorDebugThread::EnumerateChains – metoda</span><span class="sxs-lookup"><span data-stu-id="b441c-102">ICorDebugThread::EnumerateChains Method</span></span>
<span data-ttu-id="b441c-103">Získá ukazatel rozhraní na enumerátor ICorDebugChainEnum, který obsahuje všechny řetězy zásobníku v tomto objektu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="b441c-103">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b441c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b441c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b441c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b441c-105">Parameters</span></span>  
 `ppChains`  
 <span data-ttu-id="b441c-106">mimo Ukazatel na adresu `ICorDebugChainEnum` objektu, který umožňuje vyčíslení všech řetězů zásobníku v tomto vlákně počínaje aktivním řetězcem (to znamená nejnovější).</span><span class="sxs-lookup"><span data-stu-id="b441c-106">[out] A pointer to the address of an `ICorDebugChainEnum` object that allows enumeration of all the stack chains in this thread, starting at the active (that is, the most recent) chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b441c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b441c-107">Remarks</span></span>  
 <span data-ttu-id="b441c-108">Řetěz zásobníku představuje fyzický zásobník volání pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="b441c-108">The stack chain represents the physical call stack for the thread.</span></span> <span data-ttu-id="b441c-109">V následujících případech se vytvoří hranice řetězu zásobníku:</span><span class="sxs-lookup"><span data-stu-id="b441c-109">The following circumstances create a stack chain boundary:</span></span>  
  
- <span data-ttu-id="b441c-110">Přechod z spravovaného do nespravovaného nebo nespravovaného na nespravovaný.</span><span class="sxs-lookup"><span data-stu-id="b441c-110">A managed-to-unmanaged or unmanaged-to-managed transition.</span></span>  
  
- <span data-ttu-id="b441c-111">Kontextový přepínač.</span><span class="sxs-lookup"><span data-stu-id="b441c-111">A context switch.</span></span>  
  
- <span data-ttu-id="b441c-112">Napadení ladicího programu v uživatelském vlákně.</span><span class="sxs-lookup"><span data-stu-id="b441c-112">A debugger hijacking of a user thread.</span></span>  
  
 <span data-ttu-id="b441c-113">V jednoduchém případě pro vlákno, které spouští čistě spravovaný kód v jednom kontextu, bude existovat korespondence 1:1 mezi vlákny a řetězy zásobníku.</span><span class="sxs-lookup"><span data-stu-id="b441c-113">In the simple case for a thread that is running purely managed code in a single context, a one-to-one correspondence will exist between threads and stack chains.</span></span>  
  
 <span data-ttu-id="b441c-114">Ladicí program může chtít změnit uspořádání fyzických zásobníků volání všech vláken do logických zásobníků volání.</span><span class="sxs-lookup"><span data-stu-id="b441c-114">A debugger may want to rearrange the physical call stacks of all threads into logical call stacks.</span></span> <span data-ttu-id="b441c-115">To by mělo zahrnovat řazení všech zřetězení vláken podle jejich vztahů volající/volaný a jejich přeseskupování.</span><span class="sxs-lookup"><span data-stu-id="b441c-115">This would involve sorting all the threads' chains by their caller/callee relationships and regrouping them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b441c-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b441c-116">Requirements</span></span>  
 <span data-ttu-id="b441c-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b441c-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b441c-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b441c-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b441c-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b441c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b441c-120">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b441c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
