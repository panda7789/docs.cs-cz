---
title: Vlastnosti rozhraní (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: bfa03c7ebe82f3f6a03666d908a5fa9d4e386172
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325406"
---
# <a name="interface-properties-c-programming-guide"></a>Vlastnosti rozhraní (Průvodce programováním v C#)
Vlastnosti lze deklarovat na [rozhraní](../../../csharp/language-reference/keywords/interface.md). Následuje příklad přistupující objekt indexer rozhraní:  
  
 [!code-csharp[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_1.cs)]  
  
 Přistupující objekt vlastnosti rozhraní nemá text. Účelem přístupové objekty tedy k označení, zda je vlastnost pro čtení a zápis, jen pro čtení nebo jen pro zápis.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu rozhraní `IEmployee` má vlastnost pro čtení a zápis, `Name`a vlastnost určenou jen pro čtení, `Counter`. Třída `Employee` implementuje `IEmployee` rozhraní a používá tyto dvě vlastnosti. Program načte název nového zaměstnance a aktuální počet zaměstnanců a zobrazí zaměstnanec název a číslo počítaný.  
  
 Můžete použít plně kvalifikovaný název vlastnosti, která odkazuje na rozhraní, ve kterém je deklarovaná člena. Příklad:  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 To se označuje jako [explicitní implementace rozhraní](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md). Například pokud třída `Employee` je implementace dvě rozhraní `ICitizen` a `IEmployee` a mít obě rozhraní `Name` vlastnost člena implementace explicitního rozhraní bude nutné. To znamená, deklarace následující vlastnosti:  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 implementuje `Name` vlastnost `IEmployee` rozhraní při následující prohlášení:  
  
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
