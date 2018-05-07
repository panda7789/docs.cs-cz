---
title: Zápis dotazů LINQ v C#
description: Tom, jak psát dotazy.
ms.date: 12/1/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: a9683dbf3c4101829054477824ccc7135f20f535
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="write-linq-queries-in-c"></a>Zápis dotazů LINQ v C#

Toto téma ukazuje tři způsoby, ve kterých můžete napsat dotaz LINQ v jazyku C#:  
  
1.  Použijte syntaxi dotazu.  
  
2.  Pomocí syntaxe využívající metody.  
  
3.  Použijte kombinaci syntaxe dotazů a syntaxe využívající metody.  
  
 Následující příklady ukazují několik jednoduchých dotazů LINQ s použitím každý přístup uvedených výše. Obecně platí je pravidlo k použití (1) Pokud je to možné a použijte (2) a (3), kdykoli je to nezbytné.  
  
> [!NOTE]
>  Tyto dotazy pracovat na kolekce v paměti jednoduchých; Základní syntaxe je ale stejná jako v technologii LINQ to Entities a technologie LINQ to XML.  
  
## <a name="example"></a>Příklad  
  
## <a name="query-syntax"></a>Syntaxe dotazu  
 Doporučeným způsobem, jak psát dotazy většina je použití *syntaxe dotazu* k vytvoření *dotaz výrazy*. Následující příklad ukazuje tři výrazy dotazů. První výraz dotazu, který ukazuje, jak filtrovat nebo omezit použitím podmínky s výsledky `where` klauzule. Vrátí všechny elementy ve zdrojové sekvence, jejichž hodnoty jsou větší než 7 nebo menší než 3. Výraz druhé, který ukazuje, jak pořadí vrácených výsledků. Třetí výraz ukazuje, jak seskupení výsledků podle klíče. Tento dotaz vrací dvě skupiny založené na první písmeno aplikace word.  
  
 [!code-csharp[csProgGuideLINQ#5](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]  
  
 Všimněte si, že je typ dotazy <xref:System.Collections.Generic.IEnumerable%601>. Všechny tyto dotazy lze zapsat pomocí `var` jak je znázorněno v následujícím příkladu:  
  
 `var query = from num in numbers...`  
  
 V každé předchozí příklad, dotazy se neprovedou ve skutečnosti dokud iterace v proměnné dotazu v `foreach` nebo jiných příkaz. Další informace najdete v tématu [Úvod do dotazů LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
## <a name="example"></a>Příklad  
  
## <a name="method-syntax"></a>Syntaxe využívající metody  
 Některé operace dotazů musí být vyjádřena jako volání metody. Nejběžnější tyto metody jsou ty, které vracejí číselné hodnoty typu singleton, jako například <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>a tak dále. Tyto metody musí vždy volat poslední v jakýkoli dotaz proto, že představují pouze jednu hodnotu a nemůže sloužit jako zdroj pro operace další dotaz. Následující příklad ukazuje volání metody ve výrazu dotazu:  
  
 [!code-csharp[csProgGuideLINQ#6](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]  
  
## <a name="example"></a>Příklad  
 Pokud metoda akce nebo Func parametry, tyto položky jsou poskytovány ve formě [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) výrazu, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideLINQ#7](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]  
  
 V předchozí dotazy okamžitě spustí jenom dotazu č. 4. Důvodem je, že vrátí jednu hodnotu a ne obecný <xref:System.Collections.Generic.IEnumerable%601> kolekce. Metoda sama musí používat `foreach` aby se Dal vypočítat jeho hodnotu.  
  
 Každý dotaz na předchozí můžete zapsat pomocí implicitní zadáním s [var](../language-reference/keywords/var.md), jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideLINQ#8](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]  
  
## <a name="example"></a>Příklad  
  
## <a name="mixed-query-and-method-syntax"></a>Smíšená syntaxe dotazů a – metoda  
 Tento příklad ukazuje způsob použití syntaxe využívající metody na výsledky dotazu klauzule. Právě uzavřete výrazu dotazu v závorkách a pak použít operátor tečky a volat metodu. V následujícím příkladu vrací dotaz #7 počet čísla, jehož hodnota je 3 až 7. Obecně platí ale je lepší ukládat výsledek volání metody do druhé proměnné. Tímto způsobem dotaz je méně pravděpodobné, že nelze zaměňovat s výsledky dotazu.  
  
 [!code-csharp[csProgGuideLINQ#9](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]  
  
 Protože 7 dotaz vrátí jednu hodnotu a není kolekce, dotaz se spustí okamžitě.  
  
 Předchozí dotaz můžete zapsat pomocí implicitní zadáním s `var`, a to takto:  
  
```csharp  
var numCount = (from num in numbers...  
```  
  
 Ho může být napsán v syntaxe využívající metody následujícím způsobem:  
  
```csharp  
var numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
 Může být napsán pomocí explicitní zadáte, následujícím způsobem:  
  
```csharp  
int numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
## <a name="see-also"></a>Viz také  
  [Návod: Zápis dotazů v C#](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)   
 [LINQ – výrazy dotazů](index.md)  
 [where – klauzule](../language-reference/keywords/where-clause.md)
