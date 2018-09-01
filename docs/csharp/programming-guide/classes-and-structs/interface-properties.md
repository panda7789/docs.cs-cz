---
title: Vlastnosti rozhraní (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: eea2bb524496a3db22146586df323437d9f84242
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396728"
---
# <a name="interface-properties-c-programming-guide"></a>Vlastnosti rozhraní (Průvodce programováním v C#)
Vlastnosti mohou být deklarovány na [rozhraní](../../../csharp/language-reference/keywords/interface.md). Následuje příklad přistupující objekt vlastnosti rozhraní:  
  
 [!code-csharp[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_1.cs)]  
  
 Přistupující objekt vlastnosti rozhraní nemá tělo. Účelem přistupující objekty tedy označující, zda je vlastnost pro čtení i zápis, jen pro čtení nebo jen pro zápis.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu rozhraní `IEmployee` má vlastnost pro čtení i zápis, `Name`a vlastnost jen pro čtení, `Counter`. Třída `Employee` implementuje `IEmployee` rozhraní a používá tyto dvě vlastnosti. Program čte název nového zaměstnance a aktuální počet zaměstnanců a zobrazí jméno zaměstnance a vypočítané číslo.  
  
 Můžete použít plně kvalifikovaný název vlastnosti, která odkazuje na rozhraní, ve kterém člen je deklarovaný. Příklad:  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 Tento postup se nazývá [explicitní implementaci rozhraní](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md). Například pokud třída `Employee` implementuje dvě rozhraní `ICitizen` a `IEmployee` a mít obě rozhraní `Name` vlastnosti, bude explicitní implementace členu rozhraní nezbytné. To znamená, následující deklarace vlastnosti:  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 implementuje `Name` vlastnost `IEmployee` rozhraní při následující deklarace:  
  
 [!code-csharp[csProgGuideProperties#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_3.cs)]  
  
 implementuje `Name` vlastnost `ICitizen` rozhraní.  
  
 [!code-csharp[csProgGuideProperties#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_4.cs)]  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a>Vzorový výstup  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Použití vlastností](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [Porovnání mezi vlastnostmi a indexery](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
 [Indexery](../../../csharp/programming-guide/indexers/index.md)  
 [Rozhraní](../../../csharp/programming-guide/interfaces/index.md)
