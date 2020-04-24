---
title: Provést seskupená spojení (LINQ v jazyce C#)
description: Naučte se provádět seskupená spojení pomocí LINQ v jazyce C#.
ms.date: 04/22/2020
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: 740a861da7dfb9653a874d5baf67eeb2030555b4
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135747"
---
# <a name="perform-grouped-joins"></a>Provádění seskupených spojení

Spojení skupiny je užitečné při vytváření hierarchických datových struktur. Vytvoří dvojici každého prvku z první kolekce se sadou korelačních prvků z druhé kolekce.

Například třída nebo relační databázová tabulka s názvem `Student` může obsahovat dvě pole: `Id` a. `Name` Druhá třída nebo relační databázová tabulka s `Course` názvem může obsahovat dvě pole `StudentId` : `CourseTitle`a. Spojení se skupinami těchto dvou zdrojů dat, které jsou založené `Student.Id` na `Course.StudentId`shodě a, by `Student` se měly seskupit do `Course` skupin s kolekcí objektů (které můžou být prázdné).

> [!NOTE]
> Každý prvek první kolekce se zobrazí v sadě výsledků spojení skupin bez ohledu na to, zda byly ve druhé kolekci nalezeny korelační prvky. V případě, že nebyly nalezeny žádné korelační prvky, sekvence korelačních prvků pro tento prvek je prázdná. Selektor výsledku proto má přístup ke všem prvkům první kolekce. To se liší od voliče výsledku v neskupinovém spojení, které nemůže přistupovat k prvkům z první kolekce, které neodpovídají žádnému typu v druhé kolekci.

> [!WARNING]
> <xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType>nemá žádný přímý ekvivalent v rámci tradičních podmínek relační databáze. Tato metoda však implementuje nadmnožinu vnitřních spojení a levé vnější spojení. Obě tyto operace lze zapsat z podmínek seskupeného spojení. Další informace najdete v tématu [operace join](../programming-guide/concepts/linq/join-operations.md) a [Entity Framework Core GroupJoin](https://docs.microsoft.com/ef/core/querying/complex-query-operators#groupjoin).

V prvním příkladu v tomto článku se dozvíte, jak provést spojení se skupinou. Druhý příklad ukazuje, jak použít připojení skupiny k vytvoření prvků XML.

## <a name="example---group-join"></a>Příklad – spojení skupin

Následující příklad provede skupinové spojení objektů `Person` typu a `Pet` na základě `Person` odpovídajícího `Pet.Owner` vlastnosti. Na rozdíl od neskupinového spojení, které by vytvořilo dvojici prvků pro každou shodu, spojení skupin vytvoří pouze jeden výsledný objekt pro každý prvek první kolekce, který v tomto příkladu je `Person` objekt. Odpovídající prvky z druhé kolekce, které jsou `Pet` v tomto příkladu objekty, jsou seskupeny do kolekce. Nakonec funkce selektor výsledku vytvoří anonymní typ pro každou shodu, která se skládá z `Person.FirstName` a kolekce `Pet` objektů.

[!code-csharp[CsLINQProgJoining#5](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]

## <a name="example---group-join-to-create-xml"></a>Příklad – připojení skupiny k vytvoření XML

Spojení skupin jsou ideální pro vytváření XML pomocí LINQ to XML. Následující příklad je podobný předchozímu příkladu s tím rozdílem, že namísto vytváření anonymních typů funkce selektor výsledku vytvoří prvky XML reprezentující připojené objekty.

[!code-csharp[CsLINQProgJoining#6](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]

## <a name="see-also"></a>Viz také

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [Provádění vnitřních spojení](perform-inner-joins.md)
- [Provedení levých vnějších spojení](perform-left-outer-joins.md)
- [Anonymní typy](../programming-guide/classes-and-structs/anonymous-types.md)
