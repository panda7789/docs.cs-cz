---
title: Podmíněné operátory s Null (Visual Basic)
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: d30d452a7c140a0c56529386b14ef3a3512df490
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722150"
---
# <a name="-and--null-conditional-operators-visual-basic"></a><span data-ttu-id="81f4f-102">?.</span><span class="sxs-lookup"><span data-stu-id="81f4f-102">?.</span></span> <span data-ttu-id="81f4f-103">a? () podmíněné operátory s null (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81f4f-103">and ?() null-conditional operators (Visual Basic)</span></span>

<span data-ttu-id="81f4f-104">Testuje hodnotu levý operand pro null (`Nothing`) před provedením přístup ke členu (`?.`) nebo indexu (`?()`) časový limit operace; vrátí `Nothing` pokud levý operand je vyhodnocen jako `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="81f4f-104">Tests the value of the left-hand operand for null (`Nothing`) before performing a member access (`?.`) or index (`?()`) operation; returns `Nothing` if the left-hand operand evaluates to `Nothing`.</span></span> <span data-ttu-id="81f4f-105">Všimněte si, že ve výrazech, které by obvykle vrací typy hodnot, null podmíněný operátor, který se vrátí <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="81f4f-105">Note that, in the expressions that would ordinarily return value types, the null-conditional operator returns a <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="81f4f-106">Tyto operátory usnadňuje psaní méně kód pro zpracování kontroly hodnoty null, zejména v případě, že sestupně do datové struktury.</span><span class="sxs-lookup"><span data-stu-id="81f4f-106">These operators help you write less code to handle null checks, especially when descending into data structures.</span></span> <span data-ttu-id="81f4f-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="81f4f-107">For example:</span></span>

```vb
Dim length As Integer? = customers?.Length  ' Nothing if customers is Nothing  
Dim first As Customer = customers?(0)  ' Nothing if customers is Nothing  
Dim count As Integer? = customers?(0)?.Orders?.Count()  ' Nothing if customers, the first customer, or Orders is Nothing  
```

<span data-ttu-id="81f4f-108">Pro porovnání alternativní kód pro první z těchto výrazů bez null podmíněného operátoru je:</span><span class="sxs-lookup"><span data-stu-id="81f4f-108">For comparison, the alternative code for the first of these expressions without a null-conditional operator is:</span></span>

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

<span data-ttu-id="81f4f-109">Podmíněné operátory s null jsou short-circuiting.</span><span class="sxs-lookup"><span data-stu-id="81f4f-109">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="81f4f-110">Pokud jedna operace v řetězci operace přístupu a index Podmíněný člen nic nespouští, zastaví rest spuštění do řetězce.</span><span class="sxs-lookup"><span data-stu-id="81f4f-110">If one operation in a chain of conditional member access and index operations returns Nothing, the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="81f4f-111">V následujícím příkladu není vyhodnocen C(E), pokud `A`, `B`, nebo `C` vyhodnotí jako Nothing.</span><span class="sxs-lookup"><span data-stu-id="81f4f-111">In the following example, C(E) isn't evaluated if `A`, `B`, or `C` evaluates to Nothing.</span></span>

```vb
A?.B?.C?(E);
```

<span data-ttu-id="81f4f-112">Další možností použití pro přístup ke členům podmíněných null je vyvoláte způsobem bezpečným pro vlákno s mnohem menším množstvím kódu.</span><span class="sxs-lookup"><span data-stu-id="81f4f-112">Another use for null-conditional member access is to invoke delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="81f4f-113">Starý způsob vyžaduje kód podobný tomuto:</span><span class="sxs-lookup"><span data-stu-id="81f4f-113">The old way requires code like the following:</span></span>  

```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```

<span data-ttu-id="81f4f-114">Nový způsob je mnohem jednodušší:</span><span class="sxs-lookup"><span data-stu-id="81f4f-114">The new way is much simpler:</span></span>  

```vb
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="81f4f-115">Nový způsob je bezpečná pro vlákno, protože kompilátor generuje kód do vyhodnocení `PropertyChanged` pouze jednou, uchovávání výsledek v dočasné proměnné.</span><span class="sxs-lookup"><span data-stu-id="81f4f-115">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="81f4f-116">Je třeba explicitně volat `Invoke` metoda vzhledem k tomu, že neexistuje žádná syntaxe vyvolání delegáta null podmíněných `PropertyChanged?(e)`.</span><span class="sxs-lookup"><span data-stu-id="81f4f-116">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>  

## <a name="see-also"></a><span data-ttu-id="81f4f-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81f4f-117">See also</span></span>

- [<span data-ttu-id="81f4f-118">Operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81f4f-118">Operators (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="81f4f-119">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="81f4f-119">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="81f4f-120">Referenční příručka jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="81f4f-120">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
