---
title: "Vícerozměrná pole (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab3a93c21ddb9541a6149967605b851ea5a50a3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="multidimensional-arrays-c-programming-guide"></a>Vícerozměrná pole (Průvodce programováním v C#)
Pole může mít více než jednou dimenzí. Například následující deklarace vytvoří dvourozměrná pole čtyři řádky a dva sloupce.  
  
 [!code-csharp[csProgGuideArrays#11](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_1.cs)]  
  
 Následující deklarace vytvoří tři pole dimensions, 4, 2 a 3.  
  
 [!code-csharp[csProgGuideArrays#12](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a>Inicializace pole  
 Pole po deklaraci, můžete inicializovat, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideArrays#13](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_3.cs)]  
  
 Také můžete inicializovat pole bez zadání pořadí.  
  
 [!code-csharp[csProgGuideArrays#14](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_4.cs)]  
  
 Pokud zvolíte možnost deklarovat proměnnou pole bez inicializace, je nutné použít `new` operátor přiřazení pole proměnnou. Použití `new` je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideArrays#15](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_5.cs)]  
  
 Následující příklad přiřadí hodnotu konkrétního pole elementu.  
  
 [!code-csharp[csProgGuideArrays#16](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_6.cs)]  
  
 Podobně v následujícím příkladu získá hodnotu elementu konkrétní pole a přiřadí ji k proměnné `elementValue`.  
  
 [!code-csharp[csProgGuideArrays#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_7.cs)]  
  
 Následující příklad kódu inicializuje elementy pole na výchozí hodnoty (s výjimkou vícenásobných polí).  
  
 [!code-csharp[csProgGuideArrays#17](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_8.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Pole](../../../csharp/programming-guide/arrays/index.md)  
 [Jednorozměrná pole](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Vícenásobná pole](../../../csharp/programming-guide/arrays/jagged-arrays.md)
