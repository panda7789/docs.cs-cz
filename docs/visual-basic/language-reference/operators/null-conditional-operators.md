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
# <a name="-and--null-conditional-operators-visual-basic"></a>?. ani? () podmíněné operátory s hodnotou null (Visual Basic)

Před provedením operace pro přístup členů (`?.`) nebo indexu (`?()`) testuje hodnotu operandu levého horního operandu pro hodnotu null (`Nothing`); Vrátí `Nothing`, je-li operand na levé straně vyhodnocen jako `Nothing`. Všimněte si, že ve výrazech, které obvykle vracejí typy hodnot, vrátí operátor null-Condition <xref:System.Nullable%601>.

Tyto operátory vám pomůžou napsat méně kódu pro zpracování kontrol s hodnotou null, zejména při seřazení do datových struktur. Příklad:

```vb
' Nothing if customers is Nothing
Dim length As Integer? = customers?.Length

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()
```

Pro porovnání alternativní kód pro první z těchto výrazů bez podmíněného operátoru null je:

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

Někdy je nutné provést akci s objektem, který může mít hodnotu null, na základě hodnoty logického člena na tomto objektu (například vlastnost Boolean `IsAllowedFreeShipping` v následujícím příkladu):

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer IsNot Nothing AndAlso customer.IsAllowedFreeShipping Then
  ApplyFreeShippingToOrders(customer)
End If
```

Můžete zkrátit kód a vyhnout se ruční kontrole null pomocí operátoru s hodnotou null, jak je znázorněno níže:

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer?.IsAllowedFreeShipping Then ApplyFreeShippingToOrders(customer)
```

Operátory podmíněné hodnotou null jsou krátkodobé okruhy.  Pokud se jedna operace v řetězci přístupu podmíněného člena a operace indexu vrátí `Nothing`, zbývající část spuštění řetězce se zastaví.  V následujícím příkladu není `C(E)` vyhodnocována, pokud `A`, `B` nebo `C` vyhodnocuje jako `Nothing`.

```vb
A?.B?.C?(E);
```

Další možností použití pro přístup s podmíněnými členy s hodnotou null je vyvolat delegáty v bezpečném vlákně s mnohem menším kódem.  Následující příklad definuje dva typy, `NewsBroadcaster` a `NewsReceiver`. Položky zpráv jsou odesílány příjemci delegáta `NewsBroadcaster.SendNews`.

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

Pokud v seznamu `SendNews` vyvolání nejsou žádné prvky, delegát `SendNews` vyvolá <xref:System.NullReferenceException>. Před nulovými podmíněnými operátory by kód podobný následujícímu byly zajištěny, že seznam volání delegáta nebyl `Nothing`:

```vb
SendNews = SendNews.Combine({SendNews, client})
If SendNews IsNot Nothing Then
   SendNews("Just in...")
End If
```

Nový způsob je mnohem jednodušší:

```vb
SendNews = SendNews.Combine({SendNews, client})
SendNews?.Invoke("Just in...")
```

Nový způsob je bezpečný pro přístup z více vláken, protože kompilátor generuje kód pro vyhodnocení `SendNews` pouze jednou a udržování výsledku v dočasné proměnné. Je nutné explicitně volat metodu `Invoke`, protože neexistuje žádná `SendNews?(String)` syntaxe vyvolání podmíněného delegáta s hodnotou null.

## <a name="see-also"></a>Viz také:

- [Operátory (Visual Basic)](index.md)
- [Průvodce programováním Visual Basic](../../../visual-basic/programming-guide/index.md)
- [Referenční příručka jazyka Visual Basic](../../../visual-basic/language-reference/index.md)
