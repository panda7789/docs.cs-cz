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
# <a name="-and--null-conditional-operators-c-and-visual-basic"></a>?. a? [] null podmíněné operátory (C# a Visual Basic)
Používá k testování pro null před provedením přístup ke členu (`?.`) nebo index (`?[]`) operaci.  Tyto operátory usnadňuje psaní, méně kód pro zpracování null kontroly, zejména pro sestupné řazení do datové struktury.  
  
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
  
 Operátory podmínky null jsou short-circuiting.  Pokud jednu operaci v řetězci operace člen podmíněného přístupu a index, vrátí hodnotu null, zbytek řetězu provádění se zastaví.  V následujícím příkladu `E` neprovede, pokud `A`, `B`, nebo `C` vyhodnocen jako null.
  
```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

```vb
A?.B?.C?.Do(E);
A?.B?.C?(E);
```  
  
 Jiný používá pro přístup ke členu podmínky null je vyvoláním delegáti bezpečným způsobem s mnohem méně kódu.  Původní způsob vyžaduje kód takto:  
  
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
PropertyChanged?.Invoke(e)  
```  

```vb
PropertyChanged?.Invoke(e)
```  
  
 Nový způsob je bezpečné pro přístup z více vláken, protože kompilátor generuje kód do vyhodnocení `PropertyChanged` pouze jednou, udržování výsledek v dočasné proměnné.  
  
 Je třeba explicitně volat `Invoke` metoda vzhledem k tomu, že neexistuje žádná syntaxe vyvolání delegáta null podmíněného `PropertyChanged?(e)`.  
  
## <a name="language-specifications"></a>Specifikace jazyka  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 Další informace najdete v tématu [referenční dokumentace jazyka Visual Basic](../../../visual-basic/language-reference/index.md).  
  
## <a name="see-also"></a>Viz také  
 [?? (operátor slučování null)](null-conditional-operator.md)  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Referenční dokumentace jazyka Visual Basic](../../../visual-basic/language-reference/index.md)  
 [Průvodce programováním v jazyce Visual Basic](../../../visual-basic/programming-guide/index.md)
