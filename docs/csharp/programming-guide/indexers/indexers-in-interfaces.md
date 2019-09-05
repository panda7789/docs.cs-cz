---
title: Indexery v rozhraních C# – Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 7f52df0283cf057c1cd6cc4fa87c0086da7e61d2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253007"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a>Indexery v rozhraní (Průvodce programováním v C#)
Indexery lze deklarovat na [rozhraní](../../language-reference/keywords/interface.md). Přistupující objekty indexerů rozhraní se liší od přístupových objektů indexerů [tříd](../../language-reference/keywords/class.md) následujícími způsoby:  
  
- Přistupující objekty rozhraní nepoužívají modifikátory.  
  
- Přistupující objekt rozhraní nemá tělo.  
  
 Proto je účel přístupového objektu označovat, zda je indexer pro čtení i zápis, jen pro čtení nebo jen pro zápis.  
  
 Následuje příklad přístupového objektu indexeru rozhraní:  
  
 [!code-csharp[csProgGuideIndexers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#3)]  
  
 Signatura indexeru se musí lišit od signatur všech ostatních indexerů deklarovaných ve stejném rozhraní.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak implementovat indexery rozhraní.  
  
 [!code-csharp[csProgGuideIndexers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#4)]  
  
 V předchozím příkladu můžete použít explicitní implementaci člena rozhraní pomocí plně kvalifikovaného názvu člena rozhraní. Příklad:  
  
```csharp  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 Plně kvalifikovaný název je však potřeba pouze k zamezení nejednoznačnosti, je-li třída implementovaná více než jedno rozhraní se stejným podpisem indexeru. Například pokud `Employee` třída implementuje dvě `ICitizen` rozhraní a `IEmployee`a obě rozhraní mají stejný podpis indexeru, je nutné implementovat explicitní implementaci člena rozhraní. To znamená následující deklaraci indexeru:  
  
```csharp  
string IEmployee.this[int index]   
{   
}   
```  
  
 implementuje indexer na `IEmployee` rozhraní a následující deklaraci:  
  
```csharp  
string ICitizen.this[int index]
{   
}   
```  
  
 implementuje indexer na `ICitizen` rozhraní.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Indexery](./index.md)
- [Vlastnosti](../classes-and-structs/properties.md)
- [Rozhraní](../interfaces/index.md)
