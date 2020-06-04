---
title: Podmíněné operátory s null
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: bffbba859968e0a050397cd9e685c142f801798a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401469"
---
# <a name="-and--null-conditional-operators-visual-basic"></a>?. ani? () podmíněné operátory s hodnotou null (Visual Basic)

`Nothing`Před provedením operace Member Access () nebo index () otestuje hodnotu operandu levého () `?.` `?()` . vrátí, `Nothing` zda je operand na levé straně vyhodnocen `Nothing` . Všimněte si, že ve výrazech, které obvykle vracejí typy hodnot, vrátí operátor null-Condition <xref:System.Nullable%601> .

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

Operátory podmíněné hodnotou null jsou krátkodobé okruhy.  Pokud se jedna operace v řetězci přístupu podmíněného člena a operace indexu vrátí `Nothing` , zbývající část spuštění řetězce se zastaví.  V následujícím příkladu `C(E)` není vyhodnocena `A` , pokud, `B` nebo `C` vyhodnocena jako `Nothing` .

```vb
A?.B?.C?(E)
```

Další možností použití pro přístup s podmíněnými členy s hodnotou null je vyvolat delegáty v bezpečném vlákně s mnohem menším kódem.  Následující příklad definuje dva typy, `NewsBroadcaster` a `NewsReceiver` . Delegáti odesílají zprávy do příjemce `NewsBroadcaster.SendNews` .

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

Pokud v seznamu vyvolání nejsou žádné prvky `SendNews` , `SendNews` delegát vyvolá <xref:System.NullReferenceException> . Před nulovými podmíněnými operátory by kód podobný následujícímu byly zajištěny, že seznam volání delegáta nebyl `Nothing` :

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

Nový způsob je bezpečný pro přístup z více vláken, protože kompilátor generuje kód pro vyhodnocení `SendNews` pouze jednou a udržuje výsledek v dočasné proměnné. Je nutné explicitně zavolat metodu, `Invoke` protože neexistuje žádná syntaxe vyvolání podmíněného delegáta s hodnotou null `SendNews?(String)` .

## <a name="see-also"></a>Viz také

- [Operátory (Visual Basic)](index.md)
- [Příručka k programování v jazyce Visual Basic](../../programming-guide/index.md)
- [Reference jazyka Visual Basic](../index.md)
