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
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44132224"
---
# <a name="-and--null-conditional-operators-c-and-visual-basic"></a>?. a? [] null podmíněné operátory (C# a Visual Basic)
Testuje hodnotu levý operand pro hodnotu null, před provedením přístup ke členu (`?.`) nebo indexu (`?[]`) časový limit operace; vrátí `null` pokud levý operand je vyhodnocen jako `null`. 

Tyto operátory usnadňuje psaní méně kód pro zpracování null kontrol, zejména pro sestupné řazení do datové struktury.  
  
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
  
 Podmíněné operátory s null jsou short-circuiting.  Pokud jedna operace v řetězci člen podmíněného přístupu a index operace vrátí hodnotu null, zbývající části řetězci provádění zastaví.  V následujícím příkladu `E` neprovede, pokud `A`, `B`, nebo `C` vyhodnotí na hodnotu null.
  
```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

```vb
A?.B?.C?.Do(E);
A?.B?.C?(E);
```  
  
 Další možností použití pro přístup ke členům podmíněných null je vyvoláním delegátů způsobem bezpečným pro vlákno s mnohem menším množstvím kódu.  Starý způsob vyžaduje kód podobný tomuto:  
  
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
  
 Nový způsob je mnohem jednodušší:  
  
```csharp
PropertyChanged?.Invoke(…)  
```  

```vb
PropertyChanged?.Invoke(…)
```  
  
 Nový způsob je bezpečná pro vlákno, protože kompilátor generuje kód do vyhodnocení `PropertyChanged` pouze jednou, uchovávání výsledek v dočasné proměnné. Je třeba explicitně volat `Invoke` metoda vzhledem k tomu, že neexistuje žádná syntaxe vyvolání delegáta null podmíněných `PropertyChanged?(e)`.  
  
## <a name="language-specifications"></a>Specifikace jazyka  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 Další informace najdete v tématu [referenční dokumentace jazyka Visual Basic](../../../visual-basic/language-reference/index.md).  
  
## <a name="see-also"></a>Viz také

- [?? (operátoru nulového sjednocení)](null-coalescing-operator.md)  
- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Průvodce programováním v jazyce Visual Basic](../../../visual-basic/programming-guide/index.md)
