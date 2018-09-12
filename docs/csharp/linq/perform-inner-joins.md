---
title: Provádění vnitřních spojení (LINQ v JAZYKU C#)
description: Zjistěte, jak k provádění vnitřních spojení pomocí jazyka LINQ v jazyce C#.
ms.date: 12/1/2016
ms.assetid: 45bceed6-f549-4114-a9b1-b44feb497742
ms.openlocfilehash: 2f6aad30dc8278ce1bb88bacc19b27deaa0288c7
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44514407"
---
# <a name="perform-inner-joins"></a>Provádění vnitřních spojení

V podmínkách relační databázi *vnitřní spojení* vytvoří sadu výsledků dotazu v které jednotlivých prvcích objektu první kolekce se zobrazí vždy jednou pro každý odpovídající prvek v druhé kolekci. Pokud prvek v první kolekce neobsahuje žádné prvky odpovídající, nezobrazí se v sadě výsledků. <xref:System.Linq.Enumerable.Join%2A> Metody, které je voláno rozhraním `join` klauzule v jazyce C#, implementuje vnitřního spojení.

Tento článek ukazuje, jak provést čtyři variace vnitřního spojení:

- Jednoduché vnitřní spojení, které souvisí prvky ze dvou zdrojů dat na základě jednoduchého klíče.

- Na základě vnitřního spojení, které prvky ze dvou zdrojů dat. souvisí *složené* klíč. Složený klíč, který je klíčem, který se skládá z více než jednu hodnotu, umožňuje korelovat prvkům založeným na více než jednu vlastnost.

- A *více spojení* v které po sobě jdoucích spojení operace se připojují k sobě navzájem.

- Vnitřní spojení, která je implementována pomocí spojení skupiny.

## <a name="example---simple-key-join"></a>Příklad – jednoduché klíče spojení

Následující příklad vytvoří dvě kolekce, které obsahují objekty dva typy definované uživatelem, `Person` a `Pet`. Použije dotaz `join` klauzule v jazyce C# tak, aby odpovídaly `Person` objekty s `Pet` objekty, jejichž `Owner` je, že `Person`. `select` Klauzule v jazyce C# definuje, jak bude vypadat výsledných objektech. Výsledné objekty v tomto příkladu jsou anonymní typy, které se skládají z křestní jméno vlastníka a zvířecí mazlíček.

[!code-csharp[CsLINQProgJoining#1](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_1.cs)]

Všimněte si, že `Person` jehož `LastName` je "Huff" se nezobrazí v sadě výsledků, protože neexistuje žádný `Pet` objekt, který má `Pet.Owner` roven `Person`.

## <a name="example---composite-key-join"></a>Příklad – složené klíče spojení

Místo korelace prvkům založeným na právě jednu vlastnost, můžete použít složený klíč k porovnání prvků na základě více vlastností. Chcete-li to provést, zadejte funkci selektoru klíče pro každou kolekci vrátit anonymního typu, který se skládá z vlastnosti, které chcete porovnat. Pokud označíte popiskem vlastnosti, musí mít stejný popisek v anonymním typu každý klíč. Vlastnosti musí být uvedena také ve stejném pořadí.

Následující příklad používá seznam `Employee` objekty a seznam `Student` objekty k určení, které zaměstnanci jsou také studentů. Oba tyto typy mají `FirstName` a `LastName` vlastnost typu <xref:System.String>. Vrátí anonymní typ, který se skládá z funkce, které vytvoří spojení klíče z každé seznamu elementů `FirstName` a `LastName` vlastnosti jednotlivých prvků. Operace spojení porovnává tyto složené klíče pro rovnost a vrátí dvojice objektů z každého seznamu, kde křestní jméno a příjmení shodují.

[!code-csharp[CsLINQProgJoining#2](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_2.cs)]

## <a name="example---multiple-join"></a>Příklad: více spojení

Libovolný počet operací spojování lze připojit k sobě navzájem provádět více připojení. Každý `join` klauzule v jazyce C# koreluje s výsledkem předchozí spojení zadaný zdroj.

Následující příklad vytvoří tři kolekce: seznam `Person` objekty, seznam `Cat` objekty a seznam `Dog` objekty.

První `join` klauzule v jazyce C# odpovídá lidí a na základě koček `Person` odpovídající objekt `Cat.Owner`. Vrátí sekvenci anonymní typy, které obsahují `Person` objektu a `Cat.Name`.

Druhá `join` klauzule v jazyce C# koreluje anonymní typy vrácených první spojení s `Dog` objektů v zadaný seznam psy, podle složený klíč skládající se z `Owner` vlastnost typu `Person`a první písmeno názvu zvířat. Vrátí sekvenci anonymní typy, které obsahují `Cat.Name` a `Dog.Name` vlastnosti z každé shodnou dvojici. Protože se jedná vnitřní spojení, jsou vráceny pouze ty objekty z prvního zdroje dat, které mají v druhý zdroj dat shoda.

[!code-csharp[CsLINQProgJoining#3](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_3.cs)]

## <a name="example---inner-join-by-using-grouped-join"></a>Příklad – vnitřní spojení pomocí seskupených spojení

Následující příklad ukazuje, jak implementovat vnitřního spojení pomocí spojení skupiny.

V `query1`, seznam `Person` objekty je připojené skupiny do seznamu `Pet` na základě objektů `Person` odpovídající `Pet.Owner` vlastnost. Spojení skupiny vytvoří kolekci zprostředkujících skupin, kde každá skupina skládá `Person` objektu a sekvencí odpovídající `Pet` objekty.

Tak, že přidáte druhý `from` klauzule dotazu, tato sekvence sekvencí je kombinovat (nebo plochý) do jedné sekvence delší dobu. Typ prvků závěrečné sekvenci je určená `select` klauzuli. V tomto příkladu, že typ je anonymní typ, který se skládá z `Person.FirstName` a `Pet.Name` vlastnosti pro každý odpovídající dvojice.

Výsledek `query1` je ekvivalentní sadu výsledků, které by byly získány pomocí `join` klauzule bez `into` k provedení vnitřního spojení. `query2` Proměnná ukazuje tento dotaz ekvivalentní.

[!code-csharp[CsLINQProgJoining#4](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_4.cs)]

## <a name="see-also"></a>Viz také:

- <xref:System.Linq.Enumerable.Join%2A>  
- <xref:System.Linq.Enumerable.GroupJoin%2A>  
- [Provádění seskupených spojení](perform-grouped-joins.md)  
- [Provedení levých vnějších spojení](perform-left-outer-joins.md)  
- [Anonymní typy](../programming-guide/classes-and-structs/anonymous-types.md)  