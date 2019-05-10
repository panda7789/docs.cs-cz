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
# <a name="-and--null-conditional-operators-visual-basic"></a>?. a? () podmíněné operátory s null (Visual Basic)

Testuje hodnotu levý operand pro null (`Nothing`) před provedením přístup ke členu (`?.`) nebo indexu (`?()`) časový limit operace; vrátí `Nothing` pokud levý operand je vyhodnocen jako `Nothing`. Všimněte si, že ve výrazech, které obvykle vrací typy hodnot, null podmíněný operátor, který se vrátí <xref:System.Nullable%601>.

Tyto operátory usnadňuje psaní méně kód pro zpracování kontroly hodnoty null, zejména v případě, že sestupně do datové struktury. Příklad:

```vb
' Nothing if customers is Nothing  
Dim length As Integer? = customers?.Length  

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()   
```

Pro porovnání alternativní kód pro první z těchto výrazů bez null podmíněného operátoru je:

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

Někdy je potřeba provést akci na objekt, který může mít hodnotu null, na základě hodnoty Boolean člen k tomuto objektu (například vlastnost typu Boolean `IsAllowedFreeShipping` v následujícím příkladu):

```vb
  Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.
  
  If customer IsNot Nothing AndAlso customer.IsAllowedFreeShipping Then
   ApplyFreeShippingToOrders(customer)
  End If
```

Můžete zkrátit váš kód a vyhnout se ručně kontrola null použitím operátoru podmíněného null následujícím způsobem:

```vb
 Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.
 
 If customer?.IsAllowedFreeShipping Then ApplyFreeShippingToOrders(customer)
```

Podmíněné operátory s null jsou short-circuiting.  Pokud jedna operace v řetězci Podmíněný člen přístup a index operace vrátí `Nothing`, zbytek zastaví provádění řetězec.  V následujícím příkladu `C(E)` není vyhodnocen, pokud `A`, `B`, nebo `C` vyhodnotí jako `Nothing`.

```vb
A?.B?.C?(E);
```

Další možností použití pro přístup ke členům podmíněných null je vyvoláte způsobem bezpečným pro vlákno s mnohem menším množstvím kódu.  Následující příklad definuje dva typy `NewsBroadcaster` a `NewsReceiver`. Příspěvky se odesílají do příjemce podle `NewsBroadcaster.SendNews` delegovat.

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

Pokud neexistují žádné prvky v `SendNews` vyvolávacím seznamu `SendNews` delegáta vyvolá výjimku <xref:System.NullReferenceException>. Před podmíněných operátorů s null, kód jako následující zajistit, že se seznamu vyvolání delegáta `Nothing`:

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

Nový způsob je bezpečná pro vlákno, protože kompilátor generuje kód do vyhodnocení `SendNews` pouze jednou, uchovávání výsledek v dočasné proměnné. Je třeba explicitně volat `Invoke` metoda vzhledem k tomu, že neexistuje žádná syntaxe vyvolání delegáta null podmíněných `SendNews?(String)`.  

## <a name="see-also"></a>Viz také:

- [Operátory (Visual Basic)](index.md)
- [Průvodce programováním v jazyce Visual Basic](../../../visual-basic/programming-guide/index.md)
- [Referenční příručka jazyka Visual Basic](../../../visual-basic/language-reference/index.md)
