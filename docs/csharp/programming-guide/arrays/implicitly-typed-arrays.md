---
title: "Implicitně typovaná pole (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], implicity-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6e60ff600a04dab47e8b0ed52dda00441e17f25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a>Implicitně typovaná pole (Průvodce programováním v C#)
Implicitně typovaná pole ve kterém je odvodit typ pole instance, můžete vytvořit z prvky určené ve inicializátor pole. Pravidla pro všechny proměnné implicitně typované platit taky pro implicitně typovaná pole. Další informace najdete v tématu [implicitně typované lokální proměnné](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
 Implicitně typovaná pole jsou obvykle použít ve výrazech dotazů společně s inicializátory objektu a kolekce a anonymní typy.  
  
 Následující příklady ukazují, jak vytvořit implicitně typovaná pole:  
  
 [!code-csharp[csProgGuideLINQ#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_1.cs)]  
  
 V předchozím příkladu Všimněte si, že se implicitně typovaná pole žádné hranaté závorky použito na levé straně příkaz inicializace. Všimněte si také, že Vícenásobná pole jsou inicializovány pomocí `new []` stejně jako dimenze jednoho pole.  
  
## <a name="implicitly-typed-arrays-in-object-initializers"></a>Implicitně typovaná pole v inicializátory objektů  
 Když vytvoříte anonymní typ, který obsahuje pole, pole musí implicitně typovaných ve inicializátoru objektu tohoto typu. V následujícím příkladu `contacts` je implicitně typovaná pole typů anonymní, z nichž každý obsahuje pole s názvem `PhoneNumbers`. Všimněte si, že `var` – klíčové slovo není použít uvnitř inicializátory objektů.  
  
 [!code-csharp[csProgGuideLINQ#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_2.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Implicitně typované lokální proměnné](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)  
 [Pole](../../../csharp/programming-guide/arrays/index.md)  
 [Anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [Inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [var](../../../csharp/language-reference/keywords/var.md)  
 [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)
