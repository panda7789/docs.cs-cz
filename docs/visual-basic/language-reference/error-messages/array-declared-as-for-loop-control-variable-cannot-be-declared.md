---
title: "Pole deklarované jako řídicí proměnná cyklu typu for nelze deklarovat s počáteční velikostí."
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords: BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef36f14d5323a4592afe59573e249d8cfb218df9
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
