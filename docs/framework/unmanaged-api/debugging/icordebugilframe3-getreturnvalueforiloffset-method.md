---
title: "ICorDebugILFrame3::GetReturnValueForILOffset – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- csharp
- vb
api_name:
- ICorDebugILFrame3.GetReturnValueForILOffset
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 06522727-5f64-4391-9331-11386883c352
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c58319de99bdd8d7cce0ea55ccb3140a31a39bd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a><span data-ttu-id="1980d-102">ICorDebugILFrame3::GetReturnValueForILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="1980d-102">ICorDebugILFrame3::GetReturnValueForILOffset Method</span></span>
<span data-ttu-id="1980d-103">Získá objekt "ICorDebugValue", který zapouzdří návratovou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="1980d-103">Gets an "ICorDebugValue" object that encapsulates the return value of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1980d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1980d-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,   
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1980d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1980d-105">Parameters</span></span>  
 `ILOffset`  
 <span data-ttu-id="1980d-106">Korekce IL.</span><span class="sxs-lookup"><span data-stu-id="1980d-106">The IL offset.</span></span> <span data-ttu-id="1980d-107">Najdete v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="1980d-107">See the Remarks section.</span></span>  
  
 `ppReturnValue`  
 <span data-ttu-id="1980d-108">Ukazatel na adresu "ICorDebugValue" rozhraní objektu, který obsahuje informace o návratovou hodnotu volání funkce.</span><span class="sxs-lookup"><span data-stu-id="1980d-108">A pointer to the address of an "ICorDebugValue" interface object that provides information about the return value of a function call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1980d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1980d-109">Remarks</span></span>  
 <span data-ttu-id="1980d-110">Tato metoda se používá spolu s [icordebugcode3::getreturnvalueliveoffset –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) metoda získat návratovou hodnotu metody.</span><span class="sxs-lookup"><span data-stu-id="1980d-110">This method is used along with the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method to get the return value of a method.</span></span> <span data-ttu-id="1980d-111">Je užitečné v případě metody, jejichž návratové hodnoty jsou ignorovány, jako v následujících příkladech dvě kódu.</span><span class="sxs-lookup"><span data-stu-id="1980d-111">It is particularly useful in the case of methods whose return values are ignored, as in the following two code examples.</span></span> <span data-ttu-id="1980d-112">První volání příklad <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metoda, ale ignoruje návratovou hodnotu metody.</span><span class="sxs-lookup"><span data-stu-id="1980d-112">The first example calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method, but ignores the method's return value.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 <span data-ttu-id="1980d-113">V druhém příkladu znázorňuje víc častých problémů při ladění.</span><span class="sxs-lookup"><span data-stu-id="1980d-113">The second example illustrates a much more common problem in debugging.</span></span> <span data-ttu-id="1980d-114">Vzhledem k tomu, že metoda se používá jako argument při volání metody, hodnoty je dostupné jenom v případě, že ladicí program prostřednictvím vyvolání metody.</span><span class="sxs-lookup"><span data-stu-id="1980d-114">Because a method is used as an argument in a method call, its return value is accessible only when the debugger steps through the called method.</span></span> <span data-ttu-id="1980d-115">V mnoha případech zejména při vyvolání metody je definována v vnější knihovny, tento způsob není možný.</span><span class="sxs-lookup"><span data-stu-id="1980d-115">In many cases, particularly when the called method is defined in an external library, that is not possible.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 <span data-ttu-id="1980d-116">Pokud předáte [icordebugcode3::getreturnvalueliveoffset –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) metoda na IL posun k lokalitě volání funkce vrátí jeden nebo více nativní posun.</span><span class="sxs-lookup"><span data-stu-id="1980d-116">If you pass the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method an IL offset to a function call site, it returns one or more native offsets.</span></span> <span data-ttu-id="1980d-117">Ladicí program pak můžete nastavit zarážky na tyto nativní posuny ve funkci.</span><span class="sxs-lookup"><span data-stu-id="1980d-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="1980d-118">Pokud se ladicí program dotkne některé zarážce, můžete pak předejte stejnou korekce IL, který je předán tuto metodu za účelem získání návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1980d-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to get the return value.</span></span> <span data-ttu-id="1980d-119">Ladicí program by měl zrušte zaškrtnutí všech zarážek, které ji nastavit.</span><span class="sxs-lookup"><span data-stu-id="1980d-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="1980d-120">[Icordebugcode3::getreturnvalueliveoffset – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) a `ICorDebugILFrame3::GetReturnValueForILOffset` metody vám umožňují získat informace o návratovou hodnotu pro odkazové typy pouze.</span><span class="sxs-lookup"><span data-stu-id="1980d-120">The [ICorDebugCode3::GetReturnValueLiveOffset Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) and `ICorDebugILFrame3::GetReturnValueForILOffset` methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="1980d-121">Získávání informací o návratová hodnota z typů hodnot (to znamená, že všechny typy, které jsou odvozeny od <xref:System.ValueType>) není podporován.</span><span class="sxs-lookup"><span data-stu-id="1980d-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="1980d-122">Korekce IL určeného `ILOffset` parametr by měl být v lokalitě volání funkce a ladění by se měla zastavit na zarážce nastavit na nativní posunu vrácený [icordebugcode3::getreturnvalueliveoffset –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) – metoda pro stejný korekce IL.</span><span class="sxs-lookup"><span data-stu-id="1980d-122">The IL offset specified by the `ILOffset` parameter should be at a function call site, and the debuggee should be stopped at a breakpoint set at the native offset returned by the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method for the same IL offset.</span></span> <span data-ttu-id="1980d-123">Pokud ve správném umístění pro zadaný korekce IL nebyla zastavena ladění, rozhraní API se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="1980d-123">If the debuggee is not stopped at the correct location for the specified IL offset, the API will fail.</span></span>  
  
 <span data-ttu-id="1980d-124">Pokud volání funkce nevrací hodnotu, rozhraní API se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="1980d-124">If the function call doesn't return a value, the API will fail.</span></span>  
  
 <span data-ttu-id="1980d-125">`ICorDebugILFrame3::GetReturnValueForILOffset` Metoda je k dispozici pouze na základě x86 a AMD64 systémy.</span><span class="sxs-lookup"><span data-stu-id="1980d-125">The `ICorDebugILFrame3::GetReturnValueForILOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1980d-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1980d-126">Requirements</span></span>  
 <span data-ttu-id="1980d-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1980d-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1980d-128">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1980d-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1980d-129">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1980d-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1980d-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1980d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1980d-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="1980d-131">See Also</span></span>  
 [<span data-ttu-id="1980d-132">GetReturnValueLiveOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="1980d-132">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)  
 [<span data-ttu-id="1980d-133">ICorDebugILFrame3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1980d-133">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
