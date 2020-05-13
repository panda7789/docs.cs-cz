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
ms.openlocfilehash: f6a54ab9efa7ca97bcdb64afcde8812f2b5e44e9
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210069"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a><span data-ttu-id="2ffdf-102">ICorDebugILFrame3::GetReturnValueForILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="2ffdf-102">ICorDebugILFrame3::GetReturnValueForILOffset Method</span></span>
<span data-ttu-id="2ffdf-103">Získá objekt "ICorDebugValue", který zapouzdřuje vrácenou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="2ffdf-103">Gets an "ICorDebugValue" object that encapsulates the return value of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ffdf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ffdf-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ffdf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ffdf-105">Parameters</span></span>  
 `ILOffset`  
 <span data-ttu-id="2ffdf-106">Posun IL</span><span class="sxs-lookup"><span data-stu-id="2ffdf-106">The IL offset.</span></span> <span data-ttu-id="2ffdf-107">Viz část poznámky.</span><span class="sxs-lookup"><span data-stu-id="2ffdf-107">See the Remarks section.</span></span>  
  
 `ppReturnValue`  
 <span data-ttu-id="2ffdf-108">Ukazatel na adresu objektu rozhraní "ICorDebugValue", která poskytuje informace o vrácené hodnotě volání funkce.</span><span class="sxs-lookup"><span data-stu-id="2ffdf-108">A pointer to the address of an "ICorDebugValue" interface object that provides information about the return value of a function call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ffdf-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ffdf-109">Remarks</span></span>  
 <span data-ttu-id="2ffdf-110">Tato metoda se používá společně s metodou [ICorDebugCode3:: GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) pro získání návratové hodnoty metody.</span><span class="sxs-lookup"><span data-stu-id="2ffdf-110">This method is used along with the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method to get the return value of a method.</span></span> <span data-ttu-id="2ffdf-111">Je zvláště užitečné v případě metod, jejichž návratové hodnoty jsou ignorovány, jako v následujících dvou příkladech kódu.</span><span class="sxs-lookup"><span data-stu-id="2ffdf-111">It is particularly useful in the case of methods whose return values are ignored, as in the following two code examples.</span></span> <span data-ttu-id="2ffdf-112">První příklad volá <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metodu, ale ignoruje návratovou hodnotu metody.</span><span class="sxs-lookup"><span data-stu-id="2ffdf-112">The first example calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method, but ignores the method's return value.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 <span data-ttu-id="2ffdf-113">Druhý příklad ukazuje mnohem častější problém při ladění.</span><span class="sxs-lookup"><span data-stu-id="2ffdf-113">The second example illustrates a much more common problem in debugging.</span></span> <span data-ttu-id="2ffdf-114">Vzhledem k tomu, že metoda je použita jako argument ve volání metody, je její návratová hodnota přístupná pouze v případě, že ladicí program projde volanou metodou.</span><span class="sxs-lookup"><span data-stu-id="2ffdf-114">Because a method is used as an argument in a method call, its return value is accessible only when the debugger steps through the called method.</span></span> <span data-ttu-id="2ffdf-115">V mnoha případech, zejména v případě, že je volaná metoda definována v externí knihovně, to není možné.</span><span class="sxs-lookup"><span data-stu-id="2ffdf-115">In many cases, particularly when the called method is defined in an external library, that is not possible.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 <span data-ttu-id="2ffdf-116">Pokud předáte metodu [ICorDebugCode3:: GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) , posun IL na web volání funkce, vrátí jedno nebo více nativních posunů.</span><span class="sxs-lookup"><span data-stu-id="2ffdf-116">If you pass the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method an IL offset to a function call site, it returns one or more native offsets.</span></span> <span data-ttu-id="2ffdf-117">Ladicí program pak může nastavit zarážky na těchto nativních posunech ve funkci.</span><span class="sxs-lookup"><span data-stu-id="2ffdf-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="2ffdf-118">Když ladicí program narazí na jednu ze zarážek, můžete předat stejný posun IL, který jste předali do této metody, a získat tak návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2ffdf-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to get the return value.</span></span> <span data-ttu-id="2ffdf-119">Ladicí program by pak měl vymazat všechny zarážky, které nastavily.</span><span class="sxs-lookup"><span data-stu-id="2ffdf-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="2ffdf-120">[Metoda ICorDebugCode3:: GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) a `ICorDebugILFrame3::GetReturnValueForILOffset` metody umožňují získat informace o vrácených hodnotách pouze pro typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="2ffdf-120">The [ICorDebugCode3::GetReturnValueLiveOffset Method](icordebugcode3-getreturnvalueliveoffset-method.md) and `ICorDebugILFrame3::GetReturnValueForILOffset` methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="2ffdf-121">Načítání informací o vrácených hodnotách z typů hodnot (tj. všechny typy, které jsou odvozeny z <xref:System.ValueType> ), nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="2ffdf-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="2ffdf-122">Posun IL určený `ILOffset` parametrem by měl být na webu volání funkce a laděného procesu by měl být zastaven na zarážce nastavenou v nativním posunu vráceném metodou [ICorDebugCode3:: GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) pro stejný posun IL.</span><span class="sxs-lookup"><span data-stu-id="2ffdf-122">The IL offset specified by the `ILOffset` parameter should be at a function call site, and the debuggee should be stopped at a breakpoint set at the native offset returned by the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method for the same IL offset.</span></span> <span data-ttu-id="2ffdf-123">Pokud se laděného procesu nezastaví na správném místě pro zadaný posun IL, rozhraní API se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="2ffdf-123">If the debuggee is not stopped at the correct location for the specified IL offset, the API will fail.</span></span>  
  
 <span data-ttu-id="2ffdf-124">Pokud volání funkce nevrátí hodnotu, rozhraní API se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="2ffdf-124">If the function call doesn't return a value, the API will fail.</span></span>  
  
 <span data-ttu-id="2ffdf-125">Tato `ICorDebugILFrame3::GetReturnValueForILOffset` Metoda je k dispozici pouze v systémech založených na platformě x86 a amd64.</span><span class="sxs-lookup"><span data-stu-id="2ffdf-125">The `ICorDebugILFrame3::GetReturnValueForILOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ffdf-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2ffdf-126">Requirements</span></span>  
 <span data-ttu-id="2ffdf-127">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ffdf-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ffdf-128">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2ffdf-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ffdf-129">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2ffdf-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ffdf-130">**Verze .NET Framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ffdf-130">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ffdf-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ffdf-131">See also</span></span>

- [<span data-ttu-id="2ffdf-132">GetReturnValueLiveOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="2ffdf-132">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)
- [<span data-ttu-id="2ffdf-133">ICorDebugILFrame3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2ffdf-133">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
