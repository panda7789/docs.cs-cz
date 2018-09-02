---
title: Podmíněné operátory s null (C# a Visual Basic)
ms.date: 04/03/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- null-conditional operators [C#]
- null-conditional operators [Visual Basic]
- ?. operator [C#]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
ms.openlocfilehash: f00d5e489931d9c1172a21ee5f0d3e3d0a6f4a4e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43408995"
---
# <a name="-and--null-conditional-operators-c-and-visual-basic"></a><span data-ttu-id="def86-102">?.</span><span class="sxs-lookup"><span data-stu-id="def86-102">?.</span></span> <span data-ttu-id="def86-103">a? [] null podmíněné operátory (C# a Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="def86-103">and ?[] null-conditional Operators (C# and Visual Basic)</span></span>
<span data-ttu-id="def86-104">Testuje hodnotu levý operand pro hodnotu null, před provedením přístup ke členu (`?.`) nebo indexu (`?[]`) časový limit operace; vrátí `null` pokud levý operand je vyhodnocen jako `null`.</span><span class="sxs-lookup"><span data-stu-id="def86-104">Tests the value of the left-hand operand for null before performing a member access (`?.`) or index (`?[]`) operation; returns `null` if the left-hand operand evaluates to `null`.</span></span> 

<span data-ttu-id="def86-105">Tyto operátory usnadňuje psaní méně kód pro zpracování null kontrol, zejména pro sestupné řazení do datové struktury.</span><span class="sxs-lookup"><span data-stu-id="def86-105">These operators help you write less code to handle null checks, especially for descending into data structures.</span></span>  
  
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
  
 <span data-ttu-id="def86-106">Podmíněné operátory s null jsou short-circuiting.</span><span class="sxs-lookup"><span data-stu-id="def86-106">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="def86-107">Pokud jedna operace v řetězci člen podmíněného přístupu a index operace vrátí hodnotu null, zbývající části řetězci provádění zastaví.</span><span class="sxs-lookup"><span data-stu-id="def86-107">If one operation in a chain of conditional member access and index operation returns null, then the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="def86-108">V následujícím příkladu `E` neprovede, pokud `A`, `B`, nebo `C` vyhodnotí na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="def86-108">In the following example, `E` doesn't execute if `A`, `B`, or `C` evaluates to null.</span></span>
  
```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

```vb
A?.B?.C?.Do(E);
A?.B?.C?(E);
```  
  
 <span data-ttu-id="def86-109">Další možností použití pro přístup ke členům podmíněných null je vyvoláním delegátů způsobem bezpečným pro vlákno s mnohem menším množstvím kódu.</span><span class="sxs-lookup"><span data-stu-id="def86-109">Another use for the null-conditional member access is invoking delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="def86-110">Starý způsob vyžaduje kód podobný tomuto:</span><span class="sxs-lookup"><span data-stu-id="def86-110">The old way requires code like the following:</span></span>  
  
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
  
 <span data-ttu-id="def86-111">Nový způsob je mnohem jednodušší:</span><span class="sxs-lookup"><span data-stu-id="def86-111">The new way is much simpler:</span></span>  
  
```csharp
PropertyChanged?.Invoke(…)  
```  

```vb
PropertyChanged?.Invoke(…)
```  
  
 <span data-ttu-id="def86-112">Nový způsob je bezpečná pro vlákno, protože kompilátor generuje kód do vyhodnocení `PropertyChanged` pouze jednou, uchovávání výsledek v dočasné proměnné.</span><span class="sxs-lookup"><span data-stu-id="def86-112">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="def86-113">Je třeba explicitně volat `Invoke` metoda vzhledem k tomu, že neexistuje žádná syntaxe vyvolání delegáta null podmíněných `PropertyChanged?(e)`.</span><span class="sxs-lookup"><span data-stu-id="def86-113">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>  
  
## <a name="language-specifications"></a><span data-ttu-id="def86-114">Specifikace jazyka</span><span class="sxs-lookup"><span data-stu-id="def86-114">Language Specifications</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 <span data-ttu-id="def86-115">Další informace najdete v tématu [referenční dokumentace jazyka Visual Basic](../../../visual-basic/language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="def86-115">For more information, see the [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="def86-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="def86-116">See Also</span></span>

- [<span data-ttu-id="def86-117">?? (operátoru nulového sjednocení)</span><span class="sxs-lookup"><span data-stu-id="def86-117">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)  
- [<span data-ttu-id="def86-118">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="def86-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="def86-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="def86-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="def86-120">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="def86-120">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
