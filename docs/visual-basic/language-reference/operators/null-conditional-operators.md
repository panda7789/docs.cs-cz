---
title: Podmíněné operátory s Null (Visual Basic)
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: 4815fe7ad337634cfb56127fbd24a47a37fdd74b
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65062940"
---
# <a name="-and--null-conditional-operators-visual-basic"></a><span data-ttu-id="abe27-102">?.</span><span class="sxs-lookup"><span data-stu-id="abe27-102">?.</span></span> <span data-ttu-id="abe27-103">a? () podmíněné operátory s null (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="abe27-103">and ?() null-conditional operators (Visual Basic)</span></span>

<span data-ttu-id="abe27-104">Testuje hodnotu levý operand pro null (`Nothing`) před provedením přístup ke členu (`?.`) nebo indexu (`?()`) časový limit operace; vrátí `Nothing` pokud levý operand je vyhodnocen jako `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="abe27-104">Tests the value of the left-hand operand for null (`Nothing`) before performing a member access (`?.`) or index (`?()`) operation; returns `Nothing` if the left-hand operand evaluates to `Nothing`.</span></span> <span data-ttu-id="abe27-105">Všimněte si, že ve výrazech, které obvykle vrací typy hodnot, null podmíněný operátor, který se vrátí <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="abe27-105">Note that in expressions that ordinarily return value types, the null-conditional operator returns a <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="abe27-106">Tyto operátory usnadňuje psaní méně kód pro zpracování kontroly hodnoty null, zejména v případě, že sestupně do datové struktury.</span><span class="sxs-lookup"><span data-stu-id="abe27-106">These operators help you write less code to handle null checks, especially when descending into data structures.</span></span> <span data-ttu-id="abe27-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="abe27-107">For example:</span></span>

```vb
' Nothing if customers is Nothing  
Dim length As Integer? = customers?.Length  

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()   
```

<span data-ttu-id="abe27-108">Pro porovnání alternativní kód pro první z těchto výrazů bez null podmíněného operátoru je:</span><span class="sxs-lookup"><span data-stu-id="abe27-108">For comparison, the alternative code for the first of these expressions without a null-conditional operator is:</span></span>

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

<span data-ttu-id="abe27-109">Někdy je potřeba provést akci na objekt, který může mít hodnotu null, na základě hodnoty Boolean člen k tomuto objektu (například vlastnost typu Boolean `IsAllowedFreeShipping` v následujícím příkladu):</span><span class="sxs-lookup"><span data-stu-id="abe27-109">Sometimes you need to take an action on an object that may be null, based on the value of a Boolean member on that object (like the Boolean property `IsAllowedFreeShipping` in the following example):</span></span>

```vb
  Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.
  
  If customer IsNot Nothing AndAlso customer.IsAllowedFreeShipping Then
   ApplyFreeShippingToOrders(customer)
  End If
```

<span data-ttu-id="abe27-110">Můžete zkrátit váš kód a vyhnout se ručně kontrola null použitím operátoru podmíněného null následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="abe27-110">You can shorten your code and avoid manually checking for null by using the null-conditional operator as follows:</span></span>

```vb
 Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.
 
 If customer?.IsAllowedFreeShipping Then ApplyFreeShippingToOrders(customer)
```

<span data-ttu-id="abe27-111">Podmíněné operátory s null jsou short-circuiting.</span><span class="sxs-lookup"><span data-stu-id="abe27-111">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="abe27-112">Pokud jedna operace v řetězci Podmíněný člen přístup a index operace vrátí `Nothing`, zbytek zastaví provádění řetězec.</span><span class="sxs-lookup"><span data-stu-id="abe27-112">If one operation in a chain of conditional member access and index operations returns `Nothing`, the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="abe27-113">V následujícím příkladu `C(E)` není vyhodnocen, pokud `A`, `B`, nebo `C` vyhodnotí jako `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="abe27-113">In the following example, `C(E)` isn't evaluated if `A`, `B`, or `C` evaluates to `Nothing`.</span></span>

```vb
A?.B?.C?(E);
```

<span data-ttu-id="abe27-114">Další možností použití pro přístup ke členům podmíněných null je vyvoláte způsobem bezpečným pro vlákno s mnohem menším množstvím kódu.</span><span class="sxs-lookup"><span data-stu-id="abe27-114">Another use for null-conditional member access is to invoke delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="abe27-115">Následující příklad definuje dva typy `NewsBroadcaster` a `NewsReceiver`.</span><span class="sxs-lookup"><span data-stu-id="abe27-115">The following example defines two types, a `NewsBroadcaster` and a `NewsReceiver`.</span></span> <span data-ttu-id="abe27-116">Příspěvky se odesílají do příjemce podle `NewsBroadcaster.SendNews` delegovat.</span><span class="sxs-lookup"><span data-stu-id="abe27-116">News items are sent to the receiver by the `NewsBroadcaster.SendNews` delegate.</span></span>

```vb
Public Module NewsBroadcaster
   Dim SendNews As Action(Of String) 

   Public Sub Main()
      Dim rec As New NewsReceiver()
      Dim rec2 As New NewsReceiver()
      SendNews?.Invoke("Just in: A newsworthy item...")
   End Sub

   Public Sub Register(client As Action(Of String))
      SendNews = SendNews.Combine({SendNews, client})
   End Sub
End Module

Public Class NewsReceiver
   Public Sub New()
      NewsBroadcaster.Register(AddressOf Me.DisplayNews)
   End Sub

   Public Sub DisplayNews(newsItem As String)
      Console.WriteLine(newsItem)
   End Sub
End Class
```

<span data-ttu-id="abe27-117">Pokud neexistují žádné prvky v `SendNews` vyvolávacím seznamu `SendNews` delegáta vyvolá výjimku <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="abe27-117">If there are no elements in the `SendNews` invocation list, the `SendNews` delegate throws a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="abe27-118">Před podmíněných operátorů s null, kód jako následující zajistit, že se seznamu vyvolání delegáta `Nothing`:</span><span class="sxs-lookup"><span data-stu-id="abe27-118">Before null conditional operators, code like the following ensured that the delegate invocation list was not `Nothing`:</span></span>

```vb  
SendNews = SendNews.Combine({SendNews, client})  
If SendNews IsNot Nothing Then 
   SendNews("Just in...")
End If
```

<span data-ttu-id="abe27-119">Nový způsob je mnohem jednodušší:</span><span class="sxs-lookup"><span data-stu-id="abe27-119">The new way is much simpler:</span></span>  

```vb
SendNews = SendNews.Combine({SendNews, client})  
SendNews?.Invoke("Just in...")
```

<span data-ttu-id="abe27-120">Nový způsob je bezpečná pro vlákno, protože kompilátor generuje kód do vyhodnocení `SendNews` pouze jednou, uchovávání výsledek v dočasné proměnné.</span><span class="sxs-lookup"><span data-stu-id="abe27-120">The new way is thread-safe because the compiler generates code to evaluate `SendNews` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="abe27-121">Je třeba explicitně volat `Invoke` metoda vzhledem k tomu, že neexistuje žádná syntaxe vyvolání delegáta null podmíněných `SendNews?(String)`.</span><span class="sxs-lookup"><span data-stu-id="abe27-121">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `SendNews?(String)`.</span></span>  

## <a name="see-also"></a><span data-ttu-id="abe27-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="abe27-122">See also</span></span>

- [<span data-ttu-id="abe27-123">Operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="abe27-123">Operators (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="abe27-124">Průvodce programováním v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="abe27-124">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="abe27-125">Referenční příručka jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="abe27-125">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
