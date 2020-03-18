---
title: Provedení levých vnějších spojení (LINQ v C#)
description: Zjistěte, jak provádět levé vnější spojení pomocí LINQ v C#.
ms.date: 12/01/2016
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: cc08a1c8670623a10d1e0bf10221d02037a8d7bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688576"
---
# <a name="perform-left-outer-joins"></a>Provedení levých vnějších spojení

Levé vnější spojení je spojení, ve kterém je vrácena každý prvek první kolekce, bez ohledu na to, zda má všechny korelované prvky v druhé kolekci. Linq můžete použít k provedení levé vnější <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> spojení voláním metody na výsledky spojení skupiny.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> použít metodu na výsledky spojení skupiny k provedení levé vnější spojení.

Prvním krokem při vytváření levé vnější spojení dvou kolekcí je provést vnitřní spojení pomocí spojení skupiny. (Vysvětlení tohoto procesu naleznete v tématu [Provedení vnitřních spojení.)](perform-inner-joins.md) V tomto příkladu `Person` je seznam objektů vnitřní připojen `Pet` k seznamu `Person` objektů `Pet.Owner`na základě objektu, který odpovídá .

Druhým krokem je zahrnout každý prvek první (vlevo) kolekce v sadě výsledků i v případě, že tento prvek nemá žádné shody v pravé kolekci. Toho je dosaženo <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> voláním na každou sekvenci odpovídající prvky ze skupiny spojení. V tomto <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> příkladu se nazývá `Pet` na každé sekvenci odpovídající objekty. Metoda vrátí kolekci, která obsahuje jednu výchozí `Pet` hodnotu, pokud `Person` je posloupnost odpovídajících objektů prázdná pro libovolný objekt, čímž zajistí, že každý `Person` objekt je reprezentován v kolekci výsledků.

> [!NOTE]
> Výchozí hodnota pro typ `null`odkazu je ; proto příklad zkontroluje null odkaz před přístupem každý `Pet` prvek každé kolekce.

[!code-csharp[CsLINQProgJoining#7](~/samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]

## <a name="see-also"></a>Viz také

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [Provádění vnitřních spojení](perform-inner-joins.md)
- [Provádění seskupených spojení](perform-grouped-joins.md)
- [Anonymní typy](../programming-guide/classes-and-structs/anonymous-types.md)
