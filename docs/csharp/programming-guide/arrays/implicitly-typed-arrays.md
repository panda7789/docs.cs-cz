---
title: Implicitně typovaná pole (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicity-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 879955a7362af7dceda5767923c5e872cd0f6b5c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43522586"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a>Implicitně typovaná pole (Průvodce programováním v C#)

Implicitně typovaná pole ve kterém je odvozený typ pole instance můžete vytvořit z elementů zadaný v inicializátoru pole. Pravidla pro všechny implicitně typované proměnné platí také pro implicitně typovaná pole. Další informace najdete v tématu [implicitně typované lokální proměnné](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
 Implicitně typovaná pole se obvykle používají ve výrazech dotazů spolu s inicializátory objektu a kolekce a anonymní typy.  
  
 Následující příklady ukazují, jak vytvořit implicitně typované pole:  
  
 [!code-csharp[csProgGuideLINQ#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_1.cs)]  
  
 V předchozím příkladu Všimněte si, že se implicitně typovaná pole se žádné hranaté závorky používají na levé straně výrazu inicializace. Všimněte si také, že Vícenásobná pole jsou inicializovány pomocí `new []` stejně jako pole jednou dimenzí.  
  
## <a name="implicitly-typed-arrays-in-object-initializers"></a>Implicitně typovaná pole v inicializátorech objektů

 Při vytváření anonymního typu, který obsahuje pole, musí být pole implicitně typované v inicializátoru objektu tohoto typu. V následujícím příkladu `contacts` je implicitně typované pole anonymních typů, z nichž každý obsahuje pole s názvem `PhoneNumbers`. Všimněte si, `var` – klíčové slovo se nepoužívá v inicializátorech objektů.  
  
 [!code-csharp[csProgGuideLINQ#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_2.cs)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Implicitně typované lokální proměnné](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)  
- [Pole](../../../csharp/programming-guide/arrays/index.md)  
- [Anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
- [Inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
- [var](../../../csharp/language-reference/keywords/var.md)  
- [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)
