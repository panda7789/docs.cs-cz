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
# <a name="-and--null-conditional-operators-visual-basic"></a>?. a? () podmíněné operátory s null (Visual Basic)

Testuje hodnotu levý operand pro null (`Nothing`) před provedením přístup ke členu (`?.`) nebo indexu (`?()`) časový limit operace; vrátí `Nothing` pokud levý operand je vyhodnocen jako `Nothing`. Všimněte si, že ve výrazech, které by obvykle vrací typy hodnot, null podmíněný operátor, který se vrátí <xref:System.Nullable%601>.

Tyto operátory usnadňuje psaní méně kód pro zpracování kontroly hodnoty null, zejména v případě, že sestupně do datové struktury. Příklad:

```vb
Dim length As Integer? = customers?.Length  ' Nothing if customers is Nothing  
Dim first As Customer = customers?(0)  ' Nothing if customers is Nothing  
Dim count As Integer? = customers?(0)?.Orders?.Count()  ' Nothing if customers, the first customer, or Orders is Nothing  
```

Pro porovnání alternativní kód pro první z těchto výrazů bez null podmíněného operátoru je:

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

Podmíněné operátory s null jsou short-circuiting.  Pokud jedna operace v řetězci operace přístupu a index Podmíněný člen nic nespouští, zastaví rest spuštění do řetězce.  V následujícím příkladu není vyhodnocen C(E), pokud `A`, `B`, nebo `C` vyhodnotí jako Nothing.

```vb
A?.B?.C?(E);
```

Další možností použití pro přístup ke členům podmíněných null je vyvoláte způsobem bezpečným pro vlákno s mnohem menším množstvím kódu.  Starý způsob vyžaduje kód podobný tomuto:  

```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```

Nový způsob je mnohem jednodušší:  

```vb
PropertyChanged?.Invoke(…)
```

Nový způsob je bezpečná pro vlákno, protože kompilátor generuje kód do vyhodnocení `PropertyChanged` pouze jednou, uchovávání výsledek v dočasné proměnné. Je třeba explicitně volat `Invoke` metoda vzhledem k tomu, že neexistuje žádná syntaxe vyvolání delegáta null podmíněných `PropertyChanged?(e)`.  

## <a name="see-also"></a>Viz také:

- [Operátory (Visual Basic)](index.md)
- [Průvodce programováním v jazyce Visual Basic](../../../visual-basic/programming-guide/index.md)
- [Referenční příručka jazyka Visual Basic](../../../visual-basic/language-reference/index.md)
