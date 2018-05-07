---
title: Pole deklarované jako řídicí proměnná cyklu typu for nelze deklarovat s počáteční velikostí.
ms.date: 07/20/2015
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
ms.openlocfilehash: f6cf397b1e76313ab399d5e39a43ae0263df619c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a>Pole deklarované jako řídicí proměnná cyklu typu for nelze deklarovat s počáteční velikostí.
A `For Each` smyčky používá pole jako jeho *element* proměnné iterace ale inicializuje tohoto pole.  
  
 Následující příkazy ukazují, jak může být generována této chybě.  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 První `For Each` příkaz je správný způsob, jak přístup prvky `arrayList`. Druhý `For Each` příkaz vygeneruje tuto chybu.  
  
 **ID chyby:** BC32039  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Inicializace odebrání deklaraci *element* proměnné iterace.  
  
## <a name="see-also"></a>Viz také  
 [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Pole](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Kolekce](../../../standard/collections/index.md)
