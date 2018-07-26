---
title: Provádění seskupených spojení (LINQ v JAZYKU C#)
description: Zjistěte, jak k provádění seskupených spojení pomocí jazyka LINQ v jazyce C#.
ms.date: 12/1/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: d52aa8f75a1868c26f6a965553bf8047518bb447
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37403999"
---
# <a name="perform-grouped-joins"></a>Provádění seskupených spojení

Spojení skupiny je užitečné při vytváření hierarchických datové struktury. Je to dvojice každý prvek od první kolekce sadu korelační prvky z druhé kolekci.

Například třída nebo relační databázi tabulku s názvem `Student` může obsahovat dvě pole: `Id` a `Name`. Druhé třídy nebo relační databázi tabulku s názvem `Course` může obsahovat dvě pole: `StudentId` a `CourseTitle`. Skupiny spojení těchto dvou zdrojů dat, na základě porovnání `Student.Id` a `Course.StudentId`, by každé skupině `Student` sbírka `Course` objekty (které můžou být prázdné).

> [!NOTE]
> Každý prvek první kolekce se zobrazí v sadě výsledků spojení skupiny bez ohledu na to, jestli se korelační elementy nacházejí v druhé kolekci. V tomto případě se nenašly žádné korelační prvky je prázdná sekvence korelační prvků tohoto prvku. Výběr výsledku proto má přístup k každý prvek první kolekce. Tím se liší od výsledku selektoru v jiné skupině spojení, které nelze přistupovat k prvkům z první kolekce, které nemají žádná shoda v druhé kolekci.

První příklad v tomto článku se dozvíte, jak provést spojení skupiny. Druhý příklad ukazuje, jak vytvořit elementů XML pomocí spojení skupiny.

## <a name="example---group-join"></a>Příklad - Group join

Následující příklad provádí spojení skupiny objektů typu `Person` a `Pet` na základě `Person` odpovídající `Pet.Owner` vlastnost. Na rozdíl od jiných skupiny spojení, které byste mohli vytvořit dvojici prvků pro jednotlivé shody, spojení skupiny vytváří jediný výsledný objekt pro každý prvek první kolekce, která v tomto příkladu je `Person` objektu. Odpovídající prvky z druhého kolekce, které v tomto příkladu jsou `Pet` objekty, jsou seskupené do kolekce. Nakonec funkce selektor výsledek vytvoří anonymního typu pro jednotlivé shody, který se skládá z `Person.FirstName` a kolekce `Pet` objekty.

[!code-csharp[CsLINQProgJoining#5](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]

## <a name="example---group-join-to-create-xml"></a>Příklad - Group join k vytvoření XML

Group JOIN – klauzule jsou ideální pro vytváření XML pomocí LINQ to XML. Následující příklad je podobný jako předchozí příklad, s tím rozdílem, že místo vytvoření anonymní typy, funkce selektor výsledek vytvoří elementů XML, které představují připojených objektů.

[!code-csharp[CsLINQProgJoining#6](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]

## <a name="see-also"></a>Viz také:

<xref:System.Linq.Enumerable.Join%2A>  
<xref:System.Linq.Enumerable.GroupJoin%2A>  
[Provádění vnitřních spojení](perform-inner-joins.md)  
[Provedení levých vnějších spojení](perform-left-outer-joins.md)  
[Anonymní typy](../programming-guide/classes-and-structs/anonymous-types.md)  