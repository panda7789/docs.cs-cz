---
title: Indexery v rozhraních C# – Průvodce programováním
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 667a4213626ee37bfc5bf8c4fe78c2cf7186a73e
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627835"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a>Indexery v rozhraní (Průvodce programováním v C#)

Indexery lze deklarovat na [rozhraní](../../language-reference/keywords/interface.md). Přistupující objekty indexerů rozhraní se liší od přístupových objektů indexerů [tříd](../../language-reference/keywords/class.md) následujícími způsoby:

- Přistupující objekty rozhraní nepoužívají modifikátory.
- Přistupující objekt rozhraní nemá obvykle tělo.

Účelem přístupového objektu je určit, zda je indexer pro čtení i zápis, jen pro čtení nebo jen pro zápis. Můžete zadat implementaci indexeru definovaného v rozhraní, ale to je vzácné. Indexery obvykle definují rozhraní API pro přístup k datovým polím a datová pole nelze definovat v rozhraní.

Následuje příklad přístupového objektu indexeru rozhraní:

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

Signatura indexeru se musí lišit od signatur všech ostatních indexerů deklarovaných ve stejném rozhraní.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak implementovat indexery rozhraní.

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

V předchozím příkladu můžete použít explicitní implementaci člena rozhraní pomocí plně kvalifikovaného názvu člena rozhraní. Například

```csharp
string IIndexInterface.this[int index]
{
}
```

Plně kvalifikovaný název je však potřeba pouze k zamezení nejednoznačnosti, je-li třída implementovaná více než jedno rozhraní se stejným podpisem indexeru. Například pokud třída `Employee` implementuje dvě rozhraní, `ICitizen` a `IEmployee`a obě rozhraní mají stejný podpis indexeru, je nutná implementace explicitního člena rozhraní. To znamená následující deklaraci indexeru:

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

implementuje indexer na `ICitizen` rozhraní.

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Indexery](./index.md)
- [Vlastnosti](../classes-and-structs/properties.md)
- [Rozhraní](../interfaces/index.md)
