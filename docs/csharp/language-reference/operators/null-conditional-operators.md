---
title: Podmíněné operátory s null (C# a Visual Basic)
ms.date: 04/03/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
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
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3ffeaa3c2088d0bb2c000704cfe312b0f9453b68
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2018
---
# <a name="-and--null-conditional-operators-c-and-visual-basic"></a><span data-ttu-id="53fa8-102">?.</span><span class="sxs-lookup"><span data-stu-id="53fa8-102">?.</span></span> <span data-ttu-id="53fa8-103">a? [] null podmíněné operátory (C# a Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53fa8-103">and ?[] null-conditional Operators (C# and Visual Basic)</span></span>
<span data-ttu-id="53fa8-104">Používá k testování pro null před provedením přístup ke členu (`?.`) nebo index (`?[]`) operaci.</span><span class="sxs-lookup"><span data-stu-id="53fa8-104">Used to test for null before performing a member access (`?.`) or index (`?[]`) operation.</span></span>  <span data-ttu-id="53fa8-105">Tyto operátory usnadňuje psaní, méně kód pro zpracování null kontroly, zejména pro sestupné řazení do datové struktury.</span><span class="sxs-lookup"><span data-stu-id="53fa8-105">These operators help you write less code to handle null checks, especially for descending into data structures.</span></span>  
  
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
  
 <span data-ttu-id="53fa8-106">Operátory podmínky null jsou short-circuiting.</span><span class="sxs-lookup"><span data-stu-id="53fa8-106">The null-condition operators are short-circuiting.</span></span>  <span data-ttu-id="53fa8-107">Pokud jednu operaci v řetězci operace člen podmíněného přístupu a index, vrátí hodnotu null, zbytek řetězu provádění se zastaví.</span><span class="sxs-lookup"><span data-stu-id="53fa8-107">If one operation in a chain of conditional member access and index operation returns null, then the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="53fa8-108">V následujícím příkladu `E` neprovede, pokud `A`, `B`, nebo `C` vyhodnocen jako null.</span><span class="sxs-lookup"><span data-stu-id="53fa8-108">In the following example, `E` doesn't execute if `A`, `B`, or `C` evaluates to null.</span></span>
  
```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

```vb
A?.B?.C?.Do(E);
A?.B?.C?(E);
```  
  
 <span data-ttu-id="53fa8-109">Jiný používá pro přístup ke členu podmínky null je vyvoláním delegáti bezpečným způsobem s mnohem méně kódu.</span><span class="sxs-lookup"><span data-stu-id="53fa8-109">Another use for the null-condition member access is invoking delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="53fa8-110">Původní způsob vyžaduje kód takto:</span><span class="sxs-lookup"><span data-stu-id="53fa8-110">The old way requires code like the following:</span></span>  
  
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
  
 <span data-ttu-id="53fa8-111">Nový způsob je mnohem jednodušší:</span><span class="sxs-lookup"><span data-stu-id="53fa8-111">The new way is much simpler:</span></span>  
  
```csharp
PropertyChanged?.Invoke(e)  
```  

```vb
PropertyChanged?.Invoke(e)
```  
  
 <span data-ttu-id="53fa8-112">Nový způsob je bezpečné pro přístup z více vláken, protože kompilátor generuje kód do vyhodnocení `PropertyChanged` pouze jednou, udržování výsledek v dočasné proměnné.</span><span class="sxs-lookup"><span data-stu-id="53fa8-112">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span>  
  
 <span data-ttu-id="53fa8-113">Je třeba explicitně volat `Invoke` metoda vzhledem k tomu, že neexistuje žádná syntaxe vyvolání delegáta null podmíněného `PropertyChanged?(e)`.</span><span class="sxs-lookup"><span data-stu-id="53fa8-113">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>  
  
## <a name="language-specifications"></a><span data-ttu-id="53fa8-114">Specifikace jazyka</span><span class="sxs-lookup"><span data-stu-id="53fa8-114">Language Specifications</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 <span data-ttu-id="53fa8-115">Další informace najdete v tématu [referenční dokumentace jazyka Visual Basic](../../../visual-basic/language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="53fa8-115">For more information, see the [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53fa8-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="53fa8-116">See Also</span></span>  
 [<span data-ttu-id="53fa8-117">?? (operátor slučování null)</span><span class="sxs-lookup"><span data-stu-id="53fa8-117">?? (null-coalescing operator)</span></span>](null-conditional-operator.md)  
 [<span data-ttu-id="53fa8-118">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="53fa8-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="53fa8-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="53fa8-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="53fa8-120">Referenční dokumentace jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="53fa8-120">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
 [<span data-ttu-id="53fa8-121">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="53fa8-121">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
