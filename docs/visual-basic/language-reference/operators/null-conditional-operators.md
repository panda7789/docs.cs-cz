---
title: Podmíněné operátory s hodnotou null (Visual Basic)
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: 40cb63705eda563b4c3cfd30fa9836a8f632dccf
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581637"
---
# <a name="-and--null-conditional-operators-visual-basic"></a><span data-ttu-id="145bf-102">?.</span><span class="sxs-lookup"><span data-stu-id="145bf-102">?.</span></span> <span data-ttu-id="145bf-103">ani? () podmíněné operátory s hodnotou null (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="145bf-103">and ?() null-conditional operators (Visual Basic)</span></span>

<span data-ttu-id="145bf-104">Před provedením operace pro přístup členů (`?.`) nebo indexu (`?()`) testuje hodnotu operandu levého horního operandu pro hodnotu null (`Nothing`); Vrátí `Nothing`, je-li operand na levé straně vyhodnocen jako `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="145bf-104">Tests the value of the left-hand operand for null (`Nothing`) before performing a member access (`?.`) or index (`?()`) operation; returns `Nothing` if the left-hand operand evaluates to `Nothing`.</span></span> <span data-ttu-id="145bf-105">Všimněte si, že ve výrazech, které obvykle vracejí typy hodnot, vrátí operátor null-Condition <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="145bf-105">Note that in expressions that ordinarily return value types, the null-conditional operator returns a <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="145bf-106">Tyto operátory vám pomůžou napsat méně kódu pro zpracování kontrol s hodnotou null, zejména při seřazení do datových struktur.</span><span class="sxs-lookup"><span data-stu-id="145bf-106">These operators help you write less code to handle null checks, especially when descending into data structures.</span></span> <span data-ttu-id="145bf-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="145bf-107">For example:</span></span>

```vb
' Nothing if customers is Nothing
Dim length As Integer? = customers?.Length

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()
```

<span data-ttu-id="145bf-108">Pro porovnání alternativní kód pro první z těchto výrazů bez podmíněného operátoru null je:</span><span class="sxs-lookup"><span data-stu-id="145bf-108">For comparison, the alternative code for the first of these expressions without a null-conditional operator is:</span></span>

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

<span data-ttu-id="145bf-109">Někdy je nutné provést akci s objektem, který může mít hodnotu null, na základě hodnoty logického člena na tomto objektu (například vlastnost Boolean `IsAllowedFreeShipping` v následujícím příkladu):</span><span class="sxs-lookup"><span data-stu-id="145bf-109">Sometimes you need to take an action on an object that may be null, based on the value of a Boolean member on that object (like the Boolean property `IsAllowedFreeShipping` in the following example):</span></span>

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer IsNot Nothing AndAlso customer.IsAllowedFreeShipping Then
  ApplyFreeShippingToOrders(customer)
End If
```

<span data-ttu-id="145bf-110">Můžete zkrátit kód a vyhnout se ruční kontrole null pomocí operátoru s hodnotou null, jak je znázorněno níže:</span><span class="sxs-lookup"><span data-stu-id="145bf-110">You can shorten your code and avoid manually checking for null by using the null-conditional operator as follows:</span></span>

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer?.IsAllowedFreeShipping Then ApplyFreeShippingToOrders(customer)
```

<span data-ttu-id="145bf-111">Operátory podmíněné hodnotou null jsou krátkodobé okruhy.</span><span class="sxs-lookup"><span data-stu-id="145bf-111">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="145bf-112">Pokud se jedna operace v řetězci přístupu podmíněného člena a operace indexu vrátí `Nothing`, zbývající část spuštění řetězce se zastaví.</span><span class="sxs-lookup"><span data-stu-id="145bf-112">If one operation in a chain of conditional member access and index operations returns `Nothing`, the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="145bf-113">V následujícím příkladu není `C(E)` vyhodnocována, pokud `A`, `B` nebo `C` vyhodnocuje jako `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="145bf-113">In the following example, `C(E)` isn't evaluated if `A`, `B`, or `C` evaluates to `Nothing`.</span></span>

```vb
A?.B?.C?(E);
```

<span data-ttu-id="145bf-114">Další možností použití pro přístup s podmíněnými členy s hodnotou null je vyvolat delegáty v bezpečném vlákně s mnohem menším kódem.</span><span class="sxs-lookup"><span data-stu-id="145bf-114">Another use for null-conditional member access is to invoke delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="145bf-115">Následující příklad definuje dva typy, `NewsBroadcaster` a `NewsReceiver`.</span><span class="sxs-lookup"><span data-stu-id="145bf-115">The following example defines two types, a `NewsBroadcaster` and a `NewsReceiver`.</span></span> <span data-ttu-id="145bf-116">Položky zpráv jsou odesílány příjemci delegáta `NewsBroadcaster.SendNews`.</span><span class="sxs-lookup"><span data-stu-id="145bf-116">News items are sent to the receiver by the `NewsBroadcaster.SendNews` delegate.</span></span>

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

<span data-ttu-id="145bf-117">Pokud v seznamu `SendNews` vyvolání nejsou žádné prvky, delegát `SendNews` vyvolá <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="145bf-117">If there are no elements in the `SendNews` invocation list, the `SendNews` delegate throws a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="145bf-118">Před nulovými podmíněnými operátory by kód podobný následujícímu byly zajištěny, že seznam volání delegáta nebyl `Nothing`:</span><span class="sxs-lookup"><span data-stu-id="145bf-118">Before null conditional operators, code like the following ensured that the delegate invocation list was not `Nothing`:</span></span>

```vb
SendNews = SendNews.Combine({SendNews, client})
If SendNews IsNot Nothing Then
   SendNews("Just in...")
End If
```

<span data-ttu-id="145bf-119">Nový způsob je mnohem jednodušší:</span><span class="sxs-lookup"><span data-stu-id="145bf-119">The new way is much simpler:</span></span>

```vb
SendNews = SendNews.Combine({SendNews, client})
SendNews?.Invoke("Just in...")
```

<span data-ttu-id="145bf-120">Nový způsob je bezpečný pro přístup z více vláken, protože kompilátor generuje kód pro vyhodnocení `SendNews` pouze jednou a udržování výsledku v dočasné proměnné.</span><span class="sxs-lookup"><span data-stu-id="145bf-120">The new way is thread-safe because the compiler generates code to evaluate `SendNews` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="145bf-121">Je nutné explicitně volat metodu `Invoke`, protože neexistuje žádná `SendNews?(String)` syntaxe vyvolání podmíněného delegáta s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="145bf-121">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `SendNews?(String)`.</span></span>

## <a name="see-also"></a><span data-ttu-id="145bf-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="145bf-122">See also</span></span>

- [<span data-ttu-id="145bf-123">Operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="145bf-123">Operators (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="145bf-124">Průvodce programováním Visual Basic</span><span class="sxs-lookup"><span data-stu-id="145bf-124">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="145bf-125">Referenční příručka jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="145bf-125">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
