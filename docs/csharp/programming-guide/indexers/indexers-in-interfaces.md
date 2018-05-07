---
title: Indexery v rozhraní (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: cb039755b7440cbfd1f782cc118d11a03b47da04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="indexers-in-interfaces-c-programming-guide"></a>Indexery v rozhraní (Průvodce programováním v C#)
Indexery lze deklarovat na [rozhraní](../../../csharp/language-reference/keywords/interface.md). Přístupové objekty z rozhraní indexery se liší od přístupových objektů [třída](../../../csharp/language-reference/keywords/class.md) indexery následujícími způsoby:  
  
-   Přístupové objekty rozhraní nepoužívejte modifikátory.  
  
-   Přistupující objekt rozhraní nemá text.  
  
 Účelem přistupujícího objektu je proto označuje, zda indexeru pro čtení a zápis, jen pro čtení nebo jen pro zápis.  
  
 Následuje příklad přistupující objekt indexer rozhraní:  
  
 [!code-csharp[csProgGuideIndexers#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_1.cs)]  
  
 Podpis indexer se musí lišit od signatur jinými indexery deklarovaným ve stejné rozhraní.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak implementovat rozhraní indexery.  
  
 [!code-csharp[csProgGuideIndexers#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_2.cs)]  
  
 V předchozím příkladu můžete použít člen implementace explicitního rozhraní pomocí plně kvalifikovaný název člena rozhraní. Příklad:  
  
```  
public string ISomeInterface.this[int index]   
{   
}   
```  
  
 Plně kvalifikovaný název je však potřeba jenom aby se zabránilo nejednoznačnosti, když třída je implementace více než jedno rozhraní se stejným podpisem indexer. Například pokud `Employee` třída je implementace dvě rozhraní, `ICitizen` a `IEmployee`, a obě rozhraní mají stejným podpisem indexer člen implementace explicitního rozhraní je nutné. To znamená, následující prohlášení indexer:  
  
```  
public string IEmployee.this[int index]   
{   
}   
```  
  
 implementuje indexeru na `IEmployee` rozhraní při následující prohlášení:  
  
```  
public string ICitizen.this[int index]
{   
}   
```  
  
 implementuje indexeru na `ICitizen` rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Indexery](../../../csharp/programming-guide/indexers/index.md)  
 [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Rozhraní](../../../csharp/programming-guide/interfaces/index.md)
