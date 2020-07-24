---
title: Převod datových typů (C#)
description: Metody převodu mění typ vstupních objektů. Viz operace převodu v dotazech LINQ v jazyce C#, jako je například vyčíslitelné. AsEnumerable a vyčíslitelné. OfType.
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 3291690f9aaee945ca7feb04ebbc676db2612894
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105492"
---
# <a name="converting-data-types-c"></a>Převod datových typů (C#)
Metody převodu mění typ vstupních objektů.

 Operace převodu v dotazech LINQ jsou užitečné v nejrůznějších aplikacích. Následuje několik příkladů:

- <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>Metoda může být použita ke skrytí vlastní implementace typu standardního operátoru dotazu.

- <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType>Metodu lze použít k povolení neparametrizovaných kolekcí pro dotazování LINQ.

- <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>Metody, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType> , <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> a <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> lze použít k vynucení okamžitého provedení dotazu namísto jeho odložení až do vypsání dotazu.

## <a name="methods"></a>Metody
 V následující tabulce jsou uvedeny standardní metody operátoru dotazu, které provádějí převody datových typů.

 Metody převodu v této tabulce, jejichž názvy začínají znakem "as", mění statický typ zdrojové kolekce, ale nevyžadují jejich výčet. Metody, jejichž názvy začínají řetězcem "do", mají vytvořit výčet zdrojové kolekce a vkládat položky do odpovídajícího typu kolekce.

|Název metody|Popis|Syntaxe výrazu dotazu v jazyce C#|Další informace|
|-----------------|-----------------|---------------------------------|----------------------|
|AsEnumerable|Vrátí vstup zadaný jako <xref:System.Collections.Generic.IEnumerable%601> .|Neužívá se.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|AsQueryable|Převede (Obecné) <xref:System.Collections.IEnumerable> na (obecný) <xref:System.Linq.IQueryable> .|Neužívá se.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|Změna typu|Přetypování prvky kolekce na zadaný typ.|Použijte explicitně typovou proměnnou rozsahu. Příklad:<br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|Only|Filtruje hodnoty v závislosti na jejich schopnosti je přetypovat na zadaný typ.|Neužívá se.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|ToArray –|Převede kolekci na pole. Tato metoda vynutí provedení dotazu.|Neužívá se.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|ToDictionary|Vloží prvky do prvku na <xref:System.Collections.Generic.Dictionary%602> základě funkce selektoru klíče. Tato metoda vynutí provedení dotazu.|Neužívá se.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|ToList –|Převede kolekci na <xref:System.Collections.Generic.List%601> . Tato metoda vynutí provedení dotazu.|Neužívá se.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|ToLookup|Vloží prvky do <xref:System.Linq.Lookup%602> slovníku (do slovníku 1: n) na základě funkce selektoru klíče. Tato metoda vynutí provedení dotazu.|Neužívá se.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a>Příklad syntaxe výrazu dotazu

Následující příklad kódu používá explicitně typovou proměnnou rozsahu pro přetypování typu na podtyp před přístupem ke členu, který je k dispozici pouze pro podtyp.

```csharp
class Plant
{
    public string Name { get; set; }
}

class CarnivorousPlant : Plant
{
    public string TrapType { get; set; }
}

static void Cast()
{
    Plant[] plants = new Plant[] {
        new CarnivorousPlant { Name = "Venus Fly Trap", TrapType = "Snap Trap" },
        new CarnivorousPlant { Name = "Pitcher Plant", TrapType = "Pitfall Trap" },
        new CarnivorousPlant { Name = "Sundew", TrapType = "Flypaper Trap" },
        new CarnivorousPlant { Name = "Waterwheel Plant", TrapType = "Snap Trap" }
    };

    var query = from CarnivorousPlant cPlant in plants
                where cPlant.TrapType == "Snap Trap"
                select cPlant;

    foreach (Plant plant in query)
        Console.WriteLine(plant.Name);

    /* This code produces the following output:

        Venus Fly Trap
        Waterwheel Plant
    */
}
```

## <a name="see-also"></a>Viz také

- <xref:System.Linq>
- [Přehled standardních operátorů dotazů (C#)](./standard-query-operators-overview.md)
- [from – klauzule](../../../language-reference/keywords/from-clause.md)
- [Výrazy dotazů LINQ](../../../linq/index.md)
- [Postup dotazování objektu ArrayList pomocí LINQ (C#)](./how-to-query-an-arraylist-with-linq.md)
