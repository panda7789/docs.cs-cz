---
title: Indexery v rozhraní - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: c56369b28f8e1bab1ca8e8c13ebd9710c8f1d9fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61679827"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a>Indexery v rozhraní (Průvodce programováním v C#)
Indexery mohou být deklarovány na [rozhraní](../../../csharp/language-reference/keywords/interface.md). Přistupující objekty rozhraní indexery se liší od přístupových objektů [třídy](../../../csharp/language-reference/keywords/class.md) indexery následujícími způsoby:  
  
- Přístupové objekty rozhraní nepoužívejte modifikátory.  
  
- Přístupový objekt rozhraní nemá tělo.  
  
 Účelem přístupového objektu je proto udává, jestli je indexeru pro čtení i zápis, jen pro čtení nebo jen pro zápis.  
  
 Následuje příklad rozhraní indexeru přístupového objektu:  
  
 [!code-csharp[csProgGuideIndexers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#3)]  
  
 Podpis indexeru se musí lišit od podpisů ze všech indexerů je deklarována v stejné rozhraní.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak implementovat rozhraní indexery.  
  
 [!code-csharp[csProgGuideIndexers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#4)]  
  
 V předchozím příkladu můžete použít explicitní implementace členu rozhraní s použitím plně kvalifikovaný název tohoto člena rozhraní. Příklad:  
  
```  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 Plně kvalifikovaný název je však potřeba jenom k třída implementuje víc než jedno rozhraní se stejným podpisem indexer-li předejít nejednoznačnosti. Například pokud `Employee` třída implementuje dvě rozhraní, `ICitizen` a `IEmployee`, a obě rozhraní mají stejnou signaturu indexer, je nutné explicitní implementace členu rozhraní. To znamená, následující deklarace indexer:  
  
```  
string IEmployee.this[int index]   
{   
}   
```  
  
 implementuje indexer na `IEmployee` rozhraní při následující deklarace:  
  
```  
string ICitizen.this[int index]
{   
}   
```  
  
 implementuje indexer na `ICitizen` rozhraní.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Indexery](../../../csharp/programming-guide/indexers/index.md)
- [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [Rozhraní](../../../csharp/programming-guide/interfaces/index.md)
