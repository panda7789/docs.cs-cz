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
ms.openlocfilehash: 0d1ef6c1369fd399f5b36b24a21c4b5d7f1e80fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178819"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a><span data-ttu-id="fb10e-102">ICorDebugILFrame3::GetReturnValueForILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="fb10e-102">ICorDebugILFrame3::GetReturnValueForILOffset Method</span></span>
<span data-ttu-id="fb10e-103">Získá objekt "ICorDebugValue", který zapouzdřuje vrácenou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="fb10e-103">Gets an "ICorDebugValue" object that encapsulates the return value of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb10e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb10e-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb10e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb10e-105">Parameters</span></span>  
 `ILOffset`  
 <span data-ttu-id="fb10e-106">Posun IL.</span><span class="sxs-lookup"><span data-stu-id="fb10e-106">The IL offset.</span></span> <span data-ttu-id="fb10e-107">Viz část Poznámky.</span><span class="sxs-lookup"><span data-stu-id="fb10e-107">See the Remarks section.</span></span>  
  
 `ppReturnValue`  
 <span data-ttu-id="fb10e-108">Ukazatel na adresu objektu rozhraní "ICorDebugValue", který poskytuje informace o vrácené hodnotě volání funkce.</span><span class="sxs-lookup"><span data-stu-id="fb10e-108">A pointer to the address of an "ICorDebugValue" interface object that provides information about the return value of a function call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb10e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb10e-109">Remarks</span></span>  
 <span data-ttu-id="fb10e-110">Tato metoda se používá spolu s [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) metoda získat vrácenou hodnotu metody.</span><span class="sxs-lookup"><span data-stu-id="fb10e-110">This method is used along with the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method to get the return value of a method.</span></span> <span data-ttu-id="fb10e-111">To je užitečné zejména v případě metod, jejichž vrácené hodnoty jsou ignorovány, jako v následujících dvou příkladech kódu.</span><span class="sxs-lookup"><span data-stu-id="fb10e-111">It is particularly useful in the case of methods whose return values are ignored, as in the following two code examples.</span></span> <span data-ttu-id="fb10e-112">První příklad volá <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metodu, ale ignoruje vrácenou hodnotu metody.</span><span class="sxs-lookup"><span data-stu-id="fb10e-112">The first example calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method, but ignores the method's return value.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 <span data-ttu-id="fb10e-113">Druhý příklad ilustruje mnohem častější problém v ladění.</span><span class="sxs-lookup"><span data-stu-id="fb10e-113">The second example illustrates a much more common problem in debugging.</span></span> <span data-ttu-id="fb10e-114">Vzhledem k tomu, že metoda se používá jako argument ve volání metody, jeho vrácená hodnota je přístupná pouze v případě, že ladicí program kroky prostřednictvím volané metody.</span><span class="sxs-lookup"><span data-stu-id="fb10e-114">Because a method is used as an argument in a method call, its return value is accessible only when the debugger steps through the called method.</span></span> <span data-ttu-id="fb10e-115">V mnoha případech, zejména když je volaná metoda definována v externí knihovně, to není možné.</span><span class="sxs-lookup"><span data-stu-id="fb10e-115">In many cases, particularly when the called method is defined in an external library, that is not possible.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 <span data-ttu-id="fb10e-116">Pokud předáte [metodu ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) posunil IL do webu volání funkce, vrátí jeden nebo více nativních posunů.</span><span class="sxs-lookup"><span data-stu-id="fb10e-116">If you pass the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method an IL offset to a function call site, it returns one or more native offsets.</span></span> <span data-ttu-id="fb10e-117">Ladicí program pak můžete nastavit zarážky na tyto nativní posuny ve funkci.</span><span class="sxs-lookup"><span data-stu-id="fb10e-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="fb10e-118">Když ladicí program narazí na jeden z zarážek, pak můžete předat stejný posun IL, který jste předali této metodě získat vrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fb10e-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to get the return value.</span></span> <span data-ttu-id="fb10e-119">Ladicí program by pak měl vymazat všechny zarážky, které nastaví.</span><span class="sxs-lookup"><span data-stu-id="fb10e-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="fb10e-120">Metoda a `ICorDebugILFrame3::GetReturnValueForILOffset` metody [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) umožňují získat informace o vrácené hodnotě pouze pro typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="fb10e-120">The [ICorDebugCode3::GetReturnValueLiveOffset Method](icordebugcode3-getreturnvalueliveoffset-method.md) and `ICorDebugILFrame3::GetReturnValueForILOffset` methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="fb10e-121">Načítání informací o vrácené hodnotě z typů hodnot <xref:System.ValueType>(tj. všechny typy, které jsou odvozeny z ) není podporováno.</span><span class="sxs-lookup"><span data-stu-id="fb10e-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="fb10e-122">Il posun zadaný `ILOffset` parametrem by měl být v lokalitě volání funkce a ladicí zařízení by mělo být zastaveno na zarážky nastavené na nativním posunu vráceném metodou [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) pro stejný posun IL.</span><span class="sxs-lookup"><span data-stu-id="fb10e-122">The IL offset specified by the `ILOffset` parameter should be at a function call site, and the debuggee should be stopped at a breakpoint set at the native offset returned by the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method for the same IL offset.</span></span> <span data-ttu-id="fb10e-123">Pokud ladicí program není zastaven ve správném umístění pro zadaný posun IL, rozhraní API se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="fb10e-123">If the debuggee is not stopped at the correct location for the specified IL offset, the API will fail.</span></span>  
  
 <span data-ttu-id="fb10e-124">Pokud volání funkce nevrátí hodnotu, rozhraní API se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="fb10e-124">If the function call doesn't return a value, the API will fail.</span></span>  
  
 <span data-ttu-id="fb10e-125">Metoda `ICorDebugILFrame3::GetReturnValueForILOffset` je k dispozici pouze v systémech x86 a AMD64.</span><span class="sxs-lookup"><span data-stu-id="fb10e-125">The `ICorDebugILFrame3::GetReturnValueForILOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb10e-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb10e-126">Requirements</span></span>  
 <span data-ttu-id="fb10e-127">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb10e-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb10e-128">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb10e-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb10e-129">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb10e-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb10e-130">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb10e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb10e-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb10e-131">See also</span></span>

- [<span data-ttu-id="fb10e-132">GetReturnValueLiveOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="fb10e-132">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)
- [<span data-ttu-id="fb10e-133">ICorDebugILFrame3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb10e-133">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
