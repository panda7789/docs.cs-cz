---
title: Převod datových typů (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 328c790a1a360907c91f69b3b6330b0b25eb414b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347203"
---
# <a name="converting-data-types-c"></a>Převod datových typů (C#)
Metody převodu mění typ vstupních objektů.

 Operace převodu v dotazech LINQ jsou užitečné v různých aplikacích. Níže jsou uvedeny některé příklady:

- Metodu <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> lze skrýt vlastní implementaci typu standardního operátoru dotazu.

- Metodu <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> lze použít k povolení neparametrizovaných kolekcí pro dotazování LINQ.

- Metody <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType> <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> a lze vynutit okamžité spuštění dotazu namísto jeho odložení, dokud není dotaz uveden do výčtu.

## <a name="methods"></a>Metody
 V následující tabulce jsou uvedeny standardní metody operátoru dotazu, které provádějí převody datového typu.

 Metody převodu v této tabulce, jejichž názvy začínají na "As", mění statický typ zdrojové kolekce, ale nepředstavují její výčet. Metody, jejichž názvy začínají "Chcete" výčet zdrojové kolekce a umístit položky do odpovídající ho typu kolekce.

|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|
|-----------------|-----------------|---------------------------------|----------------------|
|AsEnumerable|Vrátí vstup zadaný <xref:System.Collections.Generic.IEnumerable%601>jako .|Neužívá se.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|AsQueryable|Převede (obecný) <xref:System.Collections.IEnumerable> na (obecný) <xref:System.Linq.IQueryable>.|Neužívá se.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|Změna typu|Předává prvky kolekce na zadaný typ.|Použijte explicitně zadalicí proměnnou rozsahu. Například:<br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|Oftype|Filtruje hodnoty v závislosti na jejich schopnosti přetypovat na zadaný typ.|Neužívá se.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|Toarray|Převede kolekci na pole. Tato metoda vynutí spuštění dotazu.|Neužívá se.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|ToDictionary|Vloží prvky <xref:System.Collections.Generic.Dictionary%602> do funkce voliče klíčů. Tato metoda vynutí spuštění dotazu.|Neužívá se.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|Tolist|Převede kolekci <xref:System.Collections.Generic.List%601>na . Tato metoda vynutí spuštění dotazu.|Neužívá se.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|Vyhledávání|Vloží prvky <xref:System.Linq.Lookup%602> do (slovníku 1:N) na základě funkce voliče klíčů. Tato metoda vynutí spuštění dotazu.|Neužívá se.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a>Příklad syntaxe výrazu dotazu

Následující příklad kódu používá explicitně zadaný rozsah proměnné přetypování typu podtypu před přístupem k člen, který je k dispozici pouze na podtypu.

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
- [Standardní operátory dotazů – přehled (C#)](./standard-query-operators-overview.md)
- [from – klauzule](../../../language-reference/keywords/from-clause.md)
- [Výrazy dotazu LINQ](../../../linq/index.md)
- [Jak dotaz ArrayList s LINQ (C#)](./how-to-query-an-arraylist-with-linq.md)
