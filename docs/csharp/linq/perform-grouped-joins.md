---
title: Provedení seskupených spojení (LINQ v C#)
description: Zjistěte, jak provádět seskupená spojení pomocí LINQ v C#.
ms.date: 12/01/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: dfb75b55336d8ca486d5f10b187e955d20cd06fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61689135"
---
# <a name="perform-grouped-joins"></a>Provádění seskupených spojení

Spojení skupiny je užitečné pro vytváření hierarchických datových struktur. Spáruje každý prvek z první kolekce se sadou korelovaných prvků z druhé kolekce.

Například třída nebo relační databázová tabulka s názvem `Student` může obsahovat dvě pole: `Id` a `Name`. Druhá třída nebo relační `Course` databázová tabulka `StudentId` `CourseTitle`s názvem může obsahovat dvě pole: a . Spojení skupiny těchto dvou zdrojů dat, `Course.StudentId`založené na `Student` porovnávání `Student.Id` `Course` a , by seskupit každý s kolekcí objektů (které mohou být prázdné).

> [!NOTE]
> Každý prvek první kolekce se zobrazí ve výsledkové sadě skupiny spojení bez ohledu na to, zda korelované prvky jsou nalezeny v druhé kolekci. V případě, kde jsou nalezeny žádné korelační prvky, pořadí korelovaných prvků pro tento prvek je prázdný. Volič výsledků má proto přístup ke každému prvku první kolekce. To se liší od voliče výsledků v neskupinovém spojení, které nemají přístup k prvkům z první kolekce, které nemají žádnou shodu v druhé kolekci.

První příklad v tomto článku ukazuje, jak provést připojení ke skupině. Druhý příklad ukazuje, jak pomocí skupinového spojení vytvořit elementy XML.

## <a name="example---group-join"></a>Příklad - Skupinové spojení

Následující příklad provádí skupinové spojení `Person` objektů `Pet` typu `Person` a `Pet.Owner` na základě odpovídající vlastnosti. Na rozdíl od spojení bez skupiny, které by vytvořilo dvojici prvků pro každou shodu, spojení skupiny vytvoří `Person` pouze jeden výsledný objekt pro každý prvek první kolekce, který v tomto příkladu je objekt. Odpovídající prvky z druhé kolekce, které `Pet` v tomto příkladu jsou objekty, jsou seskupeny do kolekce. Nakonec funkce selektoru výsledků vytvoří anonymní typ pro `Person.FirstName` každou shodu, která se skládá z `Pet` a kolekce objektů.

[!code-csharp[CsLINQProgJoining#5](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]

## <a name="example---group-join-to-create-xml"></a>Příklad - Seskupit spojení pro vytvoření XML

Spojení skupin jsou ideální pro vytváření XML pomocí LINQ na XML. Následující příklad je podobný předchozímu příkladu s tím rozdílem, že namísto vytváření anonymních typů vytvoří funkce selektoru výsledků elementy XML, které představují spojené objekty.

[!code-csharp[CsLINQProgJoining#6](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]

## <a name="see-also"></a>Viz také

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [Provádění vnitřních spojení](perform-inner-joins.md)
- [Provedení levých vnějších spojení](perform-left-outer-joins.md)
- [Anonymní typy](../programming-guide/classes-and-structs/anonymous-types.md)
