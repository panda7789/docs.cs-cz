---
title: "Podmíněné operátory s null (C# a Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c95b4079cf4e71c0ef9cd436ec230337f512229a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="null-conditional-operators-c-and-visual-basic"></a><span data-ttu-id="6524a-102">Podmíněné operátory s null (C# a Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6524a-102">Null-conditional Operators (C# and Visual Basic)</span></span>
<span data-ttu-id="6524a-103">Používá k testování pro null před provedením přístup ke členu (`?.`) nebo index (`?[`) operaci.</span><span class="sxs-lookup"><span data-stu-id="6524a-103">Used to test for null before performing a member access (`?.`) or index (`?[`) operation.</span></span>  <span data-ttu-id="6524a-104">Tyto operátory usnadňuje psaní, méně kód pro zpracování null kontroly, zejména pro sestupné řazení do datové struktury.</span><span class="sxs-lookup"><span data-stu-id="6524a-104">These operators help you write less code to handle null checks, especially for descending into data structures.</span></span>  
  
```csharp  
int? length = customers?.Length; // null if customers is null   
Customer first = customers?[0];  // null if customers is null  
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
```  
  
```vb  
Dim length = customers?.Length  ' null if customers is null  
Dim first as Customer = customers?(0)  ' null if customers is null  
Dim count as Integer? = customers?(0)?.Orders?.Count()  ' null if customers, the first customer, or Orders is null  
```  
  
 <span data-ttu-id="6524a-105">Poslední příklad ukazuje, že jsou short-circuiting operátory podmínky null.</span><span class="sxs-lookup"><span data-stu-id="6524a-105">The last example demonstrates that the null-condition operators are short-circuiting.</span></span>  <span data-ttu-id="6524a-106">Pokud jednu operaci v řetězci operace člen podmíněného přístupu a index, vrátí hodnotu null, zbytek řetězu provádění se zastaví.</span><span class="sxs-lookup"><span data-stu-id="6524a-106">If one operation in a chain of conditional member access and index operation returns null, then the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="6524a-107">Pokračovat v dalších operací s nižší prioritou ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="6524a-107">Other operations with lower precedence in the expression continue.</span></span>  <span data-ttu-id="6524a-108">Například `E` v následujícím spouští ve druhém řádku a `??` a `==` provedení operace.</span><span class="sxs-lookup"><span data-stu-id="6524a-108">For example, `E` in the following executes in the second line, and the `??` and `==` operations execute.</span></span>  <span data-ttu-id="6524a-109">V prvním řádku `??` krátké okruhy a `E` nespustí při na levé straně se vyhodnocuje nesmí být nulová.</span><span class="sxs-lookup"><span data-stu-id="6524a-109">In the first line, the `??` short circuits and `E` does not execute when the left side evaluates to non-null.</span></span>
  
```csharp
A?.B?.C?[0] ?? E  
A?.B?.C?[0] == E  
```

```vb
A?.B?.C?(0) ?? E  
A?.B?.C?(0) == E  
```  
  
 <span data-ttu-id="6524a-110">Jiný používá pro přístup ke členu podmínky null je vyvoláním delegáti bezpečným způsobem s mnohem méně kódu.</span><span class="sxs-lookup"><span data-stu-id="6524a-110">Another use for the null-condition member access is invoking delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="6524a-111">Původní způsob vyžaduje kód takto:</span><span class="sxs-lookup"><span data-stu-id="6524a-111">The old way requires code like the following:</span></span>  
  
```csharp  
var handler = this.PropertyChanged;  
if (handler != null)  
    handler(…);
```  
  
```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```  
  
 <span data-ttu-id="6524a-112">Nový způsob je mnohem jednodušší:</span><span class="sxs-lookup"><span data-stu-id="6524a-112">The new way is much simpler:</span></span>  
  
```csharp
PropertyChanged?.Invoke(e)  
```  

```vb
PropertyChanged?.Invoke(e)
```  
  
 <span data-ttu-id="6524a-113">Nový způsob je bezpečné pro přístup z více vláken, protože kompilátor generuje kód do vyhodnocení `PropertyChanged` pouze jednou, udržování výsledek v dočasné proměnné.</span><span class="sxs-lookup"><span data-stu-id="6524a-113">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span>  
  
 <span data-ttu-id="6524a-114">Je třeba explicitně volat `Invoke` metoda vzhledem k tomu, že neexistuje žádná syntaxe vyvolání delegáta null podmíněného `PropertyChanged?(e)`.</span><span class="sxs-lookup"><span data-stu-id="6524a-114">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>  <span data-ttu-id="6524a-115">Došlo k příliš mnoha situacích nejednoznačný analýzy tak, aby ji.</span><span class="sxs-lookup"><span data-stu-id="6524a-115">There were too many ambiguous parsing situations to allow it.</span></span>  
  
## <a name="language-specifications"></a><span data-ttu-id="6524a-116">Specifikace jazyka</span><span class="sxs-lookup"><span data-stu-id="6524a-116">Language Specifications</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 <span data-ttu-id="6524a-117">Další informace najdete v tématu [referenční dokumentace jazyka Visual Basic](../../../visual-basic/language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="6524a-117">For more information, see the [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6524a-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="6524a-118">See Also</span></span>  
 [<span data-ttu-id="6524a-119">?? (operátor slučování null)</span><span class="sxs-lookup"><span data-stu-id="6524a-119">?? (null-coalescing operator)</span></span>](null-conditional-operator.md)  
 [<span data-ttu-id="6524a-120">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6524a-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6524a-121">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="6524a-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6524a-122">Referenční dokumentace jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6524a-122">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
 [<span data-ttu-id="6524a-123">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6524a-123">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
