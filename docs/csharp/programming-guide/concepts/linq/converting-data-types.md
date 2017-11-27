---
title: "Převádění datových typů (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4733694c2a9fd7c83520b0bf2edea6ebffb47041
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="converting-data-types-c"></a>Převádění datových typů (C#)
Převod metody změnit typ vstupní objektů.  
  
 Převod operace v dotazech LINQ jsou užitečné v různých aplikací. Následuje několik příkladů:  
  
-   <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Metoda slouží ke skrytí vlastní implementaci typ operátoru standardní dotaz.  
  
-   <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> Metoda slouží k povolení-parametry kolekce pro dotazy LINQ.  
  
-   <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, A <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> metody slouží k vynucení spuštění okamžitou dotazu místo ho odložit, dokud není dotaz zpracován.  
  
## <a name="methods"></a>Metody  
 Následující tabulka uvádí metody operátor standardní dotazů, které provádět převody datových typů.  
  
 Převod metody v této tabulce, jejichž název začíná "Jako" změnit statický typ kolekce zdroj ale není výčet. Typ metody, jejichž název začíná "Na výčet zdrojové kolekci a umístí do příslušné kolekce položek".  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Jako výčet|Vrátí zadané jako vstup <xref:System.Collections.Generic.IEnumerable%601>.|Nelze použít.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|AsQueryable|Převede (Obecné) <xref:System.Collections.IEnumerable> k (Obecné) <xref:System.Linq.IQueryable>.|Nelze použít.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|Změna typu|Vrhá prvky kolekce do zadaného typu.|Pomocí proměnné explicitně typu rozsah. Příklad:<br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|OfType|Hodnoty, v závislosti na jejich schopnost převést na zadaný typ filtrování.|Nelze použít.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|ToArray|Převede kolekci na pole. Tato metoda vynutí spuštění dotazu.|Nelze použít.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|ToDictionary|Vloží elementy do <xref:System.Collections.Generic.Dictionary%602> podle funkce selektoru klíče. Tato metoda vynutí spuštění dotazu.|Nelze použít.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|ToList|Převede kolekci na <xref:System.Collections.Generic.List%601>. Tato metoda vynutí spuštění dotazu.|Nelze použít.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|ToLookup|Vloží elementy do <xref:System.Linq.Lookup%602> (slovník 1 n) podle funkce selektoru klíče. Tato metoda vynutí spuštění dotazu.|Nelze použít.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Příklad syntaxe výrazu dotazu  
 Následující příklad kódu používá proměnnou rozsahu explicitně typované přetypovat typ k podtypem před přístupem k člena, který je k dispozici pouze na dílčí.  
  
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
 <xref:System.Linq>  
 [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [from – klauzule](../../../../csharp/language-reference/keywords/from-clause.md)  
 [LINQ – výrazy dotazů](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Postupy: dotazu na ArrayList pomocí LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
