---
title: Pole deklarované jako řídicí proměnná cyklu typu for nelze deklarovat s počáteční velikostí.
ms.date: 07/20/2015
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
ms.openlocfilehash: bee3bcd3701945f5cf77f6761defc8be77acf49f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935379"
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a>Pole deklarované jako řídicí proměnná cyklu typu for nelze deklarovat s počáteční velikostí.
A `For Each` smyčky používá pole jako jeho *element* iterační proměnné ale inicializuje dané pole.  
  
 Následující příkazy ukazují, jak můžete tuto chybu vygeneruje.  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 První `For Each` příkaz je správný způsob, jak přístup prvky `arrayList`. Druhá `For Each` příkaz vygeneruje tuto chybu.  
  
 **ID chyby:** BC32039  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Odebrání inicializace deklarace *element* proměnné iterace.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Pole](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Kolekce](../../../standard/collections/index.md)
