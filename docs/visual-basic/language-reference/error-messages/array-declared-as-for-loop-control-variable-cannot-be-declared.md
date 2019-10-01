---
title: Pole deklarované jako řídicí proměnná cyklu typu for nelze deklarovat s počáteční velikostí.
ms.date: 07/20/2015
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
ms.openlocfilehash: 9e8bb7b79b5a770c3c92e47d8e7c01c5b83d6061
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701213"
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a>Pole deklarované jako řídicí proměnná cyklu typu for nelze deklarovat s počáteční velikostí.
Smyčka `For Each` používá pole jako jeho proměnnou iterace *elementu* , ale inicializuje toto pole.  
  
 Následující příkazy ukazují, jak lze tuto chybu vygenerovat.  
  
```vb  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 Prvním příkazem `For Each` je správný způsob, jak získat přístup k prvkům `arrayList`. Druhý příkaz `For Each` vygeneruje tuto chybu.  
  
 **ID chyby:** BC32039  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Odeberte inicializaci z deklarace proměnné iterace *elementu* .  
  
## <a name="see-also"></a>Viz také:

- [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Pole](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Kolekce](../../../standard/collections/index.md)
