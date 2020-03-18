---
title: Provedení vnitřních spojení (LINQ v C#)
description: Zjistěte, jak provádět vnitřní spojení pomocí LINQ v C#.
ms.date: 12/01/2016
ms.assetid: 45bceed6-f549-4114-a9b1-b44feb497742
ms.openlocfilehash: a3e8e9bd97ec630797bc48a3302b27ed45d9103e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659836"
---
# <a name="perform-inner-joins"></a>Provádění vnitřních spojení

V relační chod databáze termíny *vnitřní spojení* vytvoří sadu výsledků, ve kterém každý prvek první kolekce se zobrazí jednou pro každý odpovídající prvek v druhé kolekci. Pokud prvek v první kolekci nemá žádné odpovídající prvky, nezobrazí se v sadě výsledků. Metoda, <xref:System.Linq.Enumerable.Join%2A> která je volána `join` klauzulí v c#, implementuje vnitřní spojení.

Tento článek ukazuje, jak provést čtyři varianty vnitřního spojení:

- Jednoduché vnitřní spojení, které koreluje prvky ze dvou zdrojů dat na základě jednoduchého klíče.

- Vnitřní spojení, které koreluje prvky ze dvou zdrojů dat na základě *složeného* klíče. Složený klíč, který je klíč, který se skládá z více než jednu hodnotu, umožňuje korelovat prvky založené na více než jednu vlastnost.

- *Více násobné spojení,* ve kterém jsou vzájemně připojeny po sobě po sobě po sobě po sobě jdoucí operace spojení.

- Vnitřní spojení, které je implementováno pomocí spojení skupiny.

## <a name="example---simple-key-join"></a>Příklad - Jednoduché spojení s klíčem

Následující příklad vytvoří dvě kolekce, které obsahují objekty `Person` `Pet`dvou typů definovaných uživatelem a . Dotaz používá `join` klauzuli v c# `Pet` tak, `Owner` aby `Person`odpovídala `Person` objektům s objekty, jejichž je to . Klauzule `select` v C# definuje, jak budou výsledné objekty vypadat. V tomto příkladu výsledné objekty jsou anonymní typy, které se skládají z křestního jména vlastníka a názvu domácího mazlíčka.

[!code-csharp[CsLINQProgJoining#1](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_1.cs)]

Všimněte `Person` si, `LastName` že objekt, jehož je "Huff" `Pet` se nezobrazí v sadě výsledků, protože neexistuje žádný objekt, který má `Pet.Owner` rovno . `Person`

## <a name="example---composite-key-join"></a>Příklad - Spojení složeného klíče

Namísto korelace prvků založených pouze na jedné vlastnosti můžete použít složený klíč k porovnání prvků založených na více vlastnostech. Chcete-li to provést, zadejte funkci selektoru klíčů pro každou kolekci, chcete-li vrátit anonymní typ, který se skládá z vlastností, které chcete porovnat. Pokud označíte vlastnosti, musí mít stejný popisek v anonymním typu každého klíče. Vlastnosti se musí také zobrazit ve stejném pořadí.

Následující příklad používá seznam `Employee` objektů a `Student` seznam objektů k určení, kteří zaměstnanci jsou také studenti. Oba tyto typy `FirstName` mají `LastName` a vlastnost <xref:System.String>typu . Funkce, které vytvářejí klíče spojení z prvků každého seznamu vrátit anonymní `FirstName` `LastName` typ, který se skládá z a vlastnosti každého prvku. Operace spojení porovná tyto složené klíče pro rovnost a vrátí dvojice objektů z každého seznamu, kde se shoduje křestní jméno i příjmení.

[!code-csharp[CsLINQProgJoining#2](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_2.cs)]

## <a name="example---multiple-join"></a>Příklad – vícenásobné spojení

Libovolný počet operací spojení lze připojit k sobě navzájem provést více spojit. Každá `join` klauzule v C# koreluje zadaný zdroj dat s výsledky předchozího spojení.

Následující příklad vytvoří tři kolekce: `Person` seznam objektů, `Cat` seznam objektů a `Dog` seznam objektů.

První `join` klauzule v C# odpovídá lidem `Person` a `Cat.Owner`kočkám na základě odpovídajícího objektu . Vrátí posloupnost anonymních typů, které obsahují `Person` objekt a `Cat.Name`.

Druhá `join` klauzule v C# koreluje anonymní typy `Dog` vrácené první spojení s objekty v zadaném seznamu `Owner` psů, `Person`na základě složený klíč, který se skládá z vlastnosti typu a první písmeno názvu zvířete. Vrátí posloupnost anonymnítypy, `Cat.Name` které `Dog.Name` obsahují vlastnosti a z každé odpovídající dvojice. Vzhledem k tomu, že se jedná o vnitřní spojení, jsou vráceny pouze ty objekty z prvního zdroje dat, které mají shodu ve druhém zdroji dat.

[!code-csharp[CsLINQProgJoining#3](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_3.cs)]

## <a name="example---inner-join-by-using-grouped-join"></a>Příklad – vnitřní spojení pomocí seskupeného spojení

Následující příklad ukazuje, jak implementovat vnitřní spojení pomocí spojení skupiny.

V `query1`oblasti je `Person` seznam objektů spojen se `Pet` skupinovým seznamem objektů na základě `Person` odpovídající vlastnosti. `Pet.Owner` Spojení skupiny vytvoří kolekci zprostředkujících skupin, `Person` kde každá skupina `Pet` se skládá z objektu a posloupnosti odpovídajících objektů.

Přidáním druhé `from` klauzule do dotazu je tato sekvence kombinována (nebo sloučena) do jedné delší sekvence. Typ prvků konečné sekvence je určen klauzulí. `select` V tomto příkladu je tento typ anonymní `Person.FirstName` typ, který se skládá z vlastností a `Pet.Name` pro každou odpovídající dvojici.

Výsledek `query1` je ekvivalentní sadu výsledků, které by byly `join` získány `into` pomocí klauzule bez klauzule k provedení vnitřní spojení. Proměnná `query2` ukazuje tento ekvivalentní dotaz.

[!code-csharp[CsLINQProgJoining#4](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_4.cs)]

## <a name="see-also"></a>Viz také

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [Provádění seskupených spojení](perform-grouped-joins.md)
- [Provedení levých vnějších spojení](perform-left-outer-joins.md)
- [Anonymní typy](../programming-guide/classes-and-structs/anonymous-types.md)
