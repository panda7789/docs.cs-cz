---
title: Dynamicky určovat predikátové filtry za běhu (LINQ v C#)
description: Zjistěte, jak dynamicky určit predikátové filtry za běhu pomocí LINQ v C#.
ms.date: 12/01/2016
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: 314be8f98b9ff014f14bef11a1f3581eff8574b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659940"
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a>Dynamické určování filtrů predikátů při běhu

V některých případech nevíte až do běhu, kolik predikáty musíte použít `where` na zdrojové prvky v klauzuli. Jedním ze způsobů, jak dynamicky určit více <xref:System.Linq.Enumerable.Contains%2A> predikátových filtrů, je použití metody, jak je znázorněno v následujícím příkladu. Příklad je konstruován dvěma způsoby. Nejprve je projekt spuštěn filtrováním hodnot, které jsou k dispozici v programu. Potom je projekt spuštěn znovu pomocí vstupu za běhu.

## <a name="to-filter-by-using-the-contains-method"></a>Filtrování pomocí metody Contains

1. Otevřete novou konzolovou `PredicateFilters`aplikaci a pojmenujte ji .

2. Zkopírujte `StudentClass` třídu z [query kolekce objektů](query-a-collection-of-objects.md) a `PredicateFilters` vložte ji do oboru názvů pod třídou `Program`. `StudentClass`obsahuje seznam `Student` objektů.

3. Zakomentujte `Main` `StudentClass`metodu v .

4. Nahraďte třídu `Program` následujícím kódem:

     [!code-csharp[csProgGuideLINQ#26](~/samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]

5. Přidejte následující řádek `Main` k `DynamicPredicates`metodě ve `ids`třídě pod deklarací .

     ```csharp
     QueryById(ids);
     ```

6. Spusťte projekt.

7. V okně konzoly se zobrazí následující výstup:

     Garciová: 114

     O'Donnell: 112

     Omelčenková: 111

8. Dalším krokem je spuštění projektu znovu, tentokrát pomocí vstupu zadaného `ids`za běhu namísto pole . Změnit `QueryByID(ids)` `QueryByID(args)` na `Main` v metodě.

9. Spusťte projekt s argumenty `122 117 120 115`příkazového řádku . Při spuštění projektu se tyto hodnoty `args`stanou prvky `Main` , parametrmetody.

10. V okně konzoly se zobrazí následující výstup:

     Adamsová: 120

     Feng: 117

     Garcia: 115

     Tucker: 122

## <a name="to-filter-by-using-a-switch-statement"></a>Filtrování pomocí příkazu switch

1. Příkaz můžete `switch` použít k výběru mezi předem určenými alternativními dotazy. V následujícím příkladu `studentQuery` používá `where` jinou klauzuli v závislosti na úrovni stupně nebo rok, je určen za běhu.

2. Zkopírujte následující metodu a `DynamicPredicates`vložte ji do třídy .

     [!code-csharp[csProgGuideLINQ#27](~/samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]

3. V `Main` metodě nahraďte `QueryByID` volání následujícím voláním, které odešle první prvek z `args` pole jako svůj argument: `QueryByYear(args[0])`.

4. Spusťte projekt s argumentem příkazového řádku s hodnotou celéčíslo mezi 1 a 4.

## <a name="see-also"></a>Viz také

- [LINQ (Language Integrated Query)](index.md)
- [where – klauzule](../language-reference/keywords/where-clause.md)
