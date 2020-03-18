---
title: Indexery v rozhraních – programovací příručka Jazyka C#
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 667a4213626ee37bfc5bf8c4fe78c2cf7186a73e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627835"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a>Indexery v rozhraní (Průvodce programováním v C#)

Indexery lze deklarovat na [rozhraní](../../language-reference/keywords/interface.md). Přístupové servery indexerů rozhraní se liší od přístupových modulů indexerů [třídy](../../language-reference/keywords/class.md) následujícími způsoby:

- Přístupové moduly rozhraní nepoužívají modifikátory.
- Přístupový objekt rozhraní obvykle nemá tělo.

Účelem přistupujícího serveru je označit, zda indexer je jen pro čtení, jen pro čtení nebo jen pro zápis. Můžete poskytnout implementaci pro indexer definované v rozhraní, ale to je vzácné. Indexery obvykle definují rozhraní API pro přístup k datovým polím a datová pole nelze definovat v rozhraní.

Následuje příklad přístupového objektu indexeru rozhraní:

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

Podpis indexeru se musí lišit od podpisů všech ostatních indexerů deklarovaných ve stejném rozhraní.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak implementovat indexery rozhraní.

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

V předchozím příkladu můžete použít implementaci explicitního člena rozhraní pomocí plně kvalifikovaného názvu člena rozhraní. Například

```csharp
string IIndexInterface.this[int index]
{
}
```

Plně kvalifikovaný název je však potřeba pouze zabránit nejednoznačnosti, když třída implementuje více než jedno rozhraní se stejným podpisem indexeru. Například pokud `Employee` třída implementuje dvě `ICitizen` rozhraní `IEmployee`a , a obě rozhraní mají stejný podpis indexeru, explicitní implementace člena rozhraní je nezbytné. To znamená následující prohlášení indexeru:

```csharp
string IEmployee.this[int index]
{
}
``

implements the indexer on the `IEmployee` interface, while the following declaration:

```csharp
string ICitizen.this[int index]
{
}
```

implementuje indexer `ICitizen` na rozhraní.

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Indexery](./index.md)
- [Vlastnosti](../classes-and-structs/properties.md)
- [Rozhraní](../interfaces/index.md)
