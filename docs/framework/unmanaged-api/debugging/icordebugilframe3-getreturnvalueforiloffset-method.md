---
title: ICorDebugILFrame3::GetReturnValueForILOffset – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a01e2fcc7dc00d3a57272abb04ebcecc6d5f74a6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57467065"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a><span data-ttu-id="4a531-102">ICorDebugILFrame3::GetReturnValueForILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="4a531-102">ICorDebugILFrame3::GetReturnValueForILOffset Method</span></span>
<span data-ttu-id="4a531-103">Získá objekt "ICorDebugValue", který zapouzdřuje vrácenou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="4a531-103">Gets an "ICorDebugValue" object that encapsulates the return value of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a531-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a531-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,   
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a531-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a531-105">Parameters</span></span>  
 `ILOffset`  
 <span data-ttu-id="4a531-106">Posun IL.</span><span class="sxs-lookup"><span data-stu-id="4a531-106">The IL offset.</span></span> <span data-ttu-id="4a531-107">V části poznámky.</span><span class="sxs-lookup"><span data-stu-id="4a531-107">See the Remarks section.</span></span>  
  
 `ppReturnValue`  
 <span data-ttu-id="4a531-108">Ukazatel na adresu objektu rozhraní "ICorDebugValue", který poskytuje informace o vrácené hodnotě volání funkce.</span><span class="sxs-lookup"><span data-stu-id="4a531-108">A pointer to the address of an "ICorDebugValue" interface object that provides information about the return value of a function call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a531-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4a531-109">Remarks</span></span>  
 <span data-ttu-id="4a531-110">Tato metoda se používá spolu s [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) metodu k získání vrácené hodnoty metody.</span><span class="sxs-lookup"><span data-stu-id="4a531-110">This method is used along with the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method to get the return value of a method.</span></span> <span data-ttu-id="4a531-111">Je to užitečné zejména v případě metod, jejichž vrácené hodnoty jsou ignorovány, stejně jako v následujících dvou příkladech.</span><span class="sxs-lookup"><span data-stu-id="4a531-111">It is particularly useful in the case of methods whose return values are ignored, as in the following two code examples.</span></span> <span data-ttu-id="4a531-112">První příklad volá <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metody, ale ignoruje vrácenou hodnotu metody.</span><span class="sxs-lookup"><span data-stu-id="4a531-112">The first example calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method, but ignores the method's return value.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 <span data-ttu-id="4a531-113">Druhý příklad ukazuje mnohem častější problém v ladění.</span><span class="sxs-lookup"><span data-stu-id="4a531-113">The second example illustrates a much more common problem in debugging.</span></span> <span data-ttu-id="4a531-114">Protože metoda se používá jako argument ve volání metody, vrácená hodnota je dostupná jenom v případě, že ladicí program projde volané metody.</span><span class="sxs-lookup"><span data-stu-id="4a531-114">Because a method is used as an argument in a method call, its return value is accessible only when the debugger steps through the called method.</span></span> <span data-ttu-id="4a531-115">V mnoha případech zejména pokud volaná metoda je definována v externí knihovně, která není možné.</span><span class="sxs-lookup"><span data-stu-id="4a531-115">In many cases, particularly when the called method is defined in an external library, that is not possible.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 <span data-ttu-id="4a531-116">Pokud předáte [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) metoda posun IL na funkci volání webu, vrátí jeden nebo více nativních posunů.</span><span class="sxs-lookup"><span data-stu-id="4a531-116">If you pass the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method an IL offset to a function call site, it returns one or more native offsets.</span></span> <span data-ttu-id="4a531-117">Ladicí program může potom nastavit zarážky u těchto nativních posunů funkce.</span><span class="sxs-lookup"><span data-stu-id="4a531-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="4a531-118">Pokud ladicí program narazí na jednu ze zarážek, které můžete předat stejné odsazení IL, které jste předali do této metody k získání vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4a531-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to get the return value.</span></span> <span data-ttu-id="4a531-119">Ladicí program by měl poté zrušit všechny zarážky, které nastavil.</span><span class="sxs-lookup"><span data-stu-id="4a531-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="4a531-120">[ICorDebugCode3::GetReturnValueLiveOffset Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) a `ICorDebugILFrame3::GetReturnValueForILOffset` metody umožňují získat informace o vrácené hodnotě pouze pro typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="4a531-120">The [ICorDebugCode3::GetReturnValueLiveOffset Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) and `ICorDebugILFrame3::GetReturnValueForILOffset` methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="4a531-121">Načítají se informace o vrácené hodnotě z typů hodnot (to znamená, že všechny typy, které jsou odvozeny z <xref:System.ValueType>) se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="4a531-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="4a531-122">Posun IL určený parametrem `ILOffset` parametr by měl být v místě volání funkce a laděný proces by měl být zastaven na zarážce nastavené pro nativní posun vrácený metodou [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) – metoda pro stejný posun IL.</span><span class="sxs-lookup"><span data-stu-id="4a531-122">The IL offset specified by the `ILOffset` parameter should be at a function call site, and the debuggee should be stopped at a breakpoint set at the native offset returned by the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method for the same IL offset.</span></span> <span data-ttu-id="4a531-123">Pokud laděná položka není zastavená na správném umístění pro zadaný posun IL, rozhraní API se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="4a531-123">If the debuggee is not stopped at the correct location for the specified IL offset, the API will fail.</span></span>  
  
 <span data-ttu-id="4a531-124">Pokud volání funkce nevrací hodnotu, rozhraní API se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="4a531-124">If the function call doesn't return a value, the API will fail.</span></span>  
  
 <span data-ttu-id="4a531-125">`ICorDebugILFrame3::GetReturnValueForILOffset` Metoda je k dispozici pouze na základě x86 a AMD64 systémy.</span><span class="sxs-lookup"><span data-stu-id="4a531-125">The `ICorDebugILFrame3::GetReturnValueForILOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a531-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4a531-126">Requirements</span></span>  
 <span data-ttu-id="4a531-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a531-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a531-128">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a531-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a531-129">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a531-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a531-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a531-130">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a531-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a531-131">See also</span></span>
- [<span data-ttu-id="4a531-132">GetReturnValueLiveOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="4a531-132">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)
- [<span data-ttu-id="4a531-133">ICorDebugILFrame3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a531-133">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
