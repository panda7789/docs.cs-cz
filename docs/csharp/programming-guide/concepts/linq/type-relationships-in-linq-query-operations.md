---
title: Vztahy typů v operacích dotazu LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- inferring type information [LINQ in C#]
- data sources [LINQ in C#], type relationships
- queries [LINQ in C#], type relationships
- relationships [LINQ in C#]
- type relationships [LINQ in C#]
- variable relationships [LINQ in C#]
- type information inferred [LINQ in C#]
- data transformations [LINQ in C#]
- LINQ [C#], type relationships
ms.assetid: 99118938-d47c-4d7e-bb22-2657a9f95268
ms.openlocfilehash: 41853e6858fae9e8d449aeed95a6a84f343d5874
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635610"
---
# <a name="type-relationships-in-linq-query-operations-c"></a>Vztahy typů v operacích dotazu LINQ (C#)
Chcete-li psát dotazy efektivně, měli byste pochopit, jak typy proměnných v operaci úplnédotaz všechny vzájemně souvisejí. Pokud rozumíte těmto vztahům, budete snadněji pochopit linq ukázky a příklady kódu v dokumentaci. Kromě toho pochopíte, co se děje na pozadí, když proměnné `var`implicitně zadali pomocí .  
  
 Linq operace dotazu jsou silně zadali ve zdroji dat, v samotném dotazu a v provádění dotazu. Typ proměnných v dotazu musí být kompatibilní s typem prvků ve zdroji dat a s `foreach` typem iterace proměnné v příkazu. Toto silné psaní zaručuje, že chyby typu jsou zachyceny v době kompilace, kdy je lze opravit dříve, než se s nimi uživatelé setkají.  
  
 Chcete-li demonstrovat tyto vztahy typu, většina příkladů, které následují použít explicitní psaní pro všechny proměnné. Poslední příklad ukazuje, jak platí stejné zásady i v případě, že používáte implicitní psaní pomocí [var](../../../language-reference/keywords/var.md).  
  
## <a name="queries-that-do-not-transform-the-source-data"></a>Dotazy, které netransformují zdrojová data  
 Následující obrázek znázorňuje operaci dotazu LINQ to Objects, která neprovádí žádné transformace na data. Zdroj obsahuje posloupnost řetězců a výstup dotazu je také posloupnost řetězců.  
  
 ![Diagram, který zobrazuje vztah datových typů v dotazu LINQ.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. Typ argumentu zdroje dat určuje typ proměnné rozsahu.  
  
2. Typ vybraného objektu určuje typ proměnné dotazu. Tady `name` je provázek. Proměnná dotazu je `IEnumerable<string>`proto .  
  
3. Proměnná dotazu je v `foreach` příkazu iterována. Vzhledem k tomu, že proměnná dotazu je posloupnost řetězců, itidati proměnná je také řetězec.  
  
## <a name="queries-that-transform-the-source-data"></a>Dotazy, které transformují zdrojová data  
 Následující obrázek [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] znázorňuje operaci dotazu, která provádí jednoduchou transformaci dat. Dotaz přebírá posloupnost `Customer` objektů jako vstup a `Name` vybere pouze vlastnost ve výsledku. Protože `Name` je řetězec, dotaz vytvoří posloupnost řetězců jako výstup.  
  
 ![Diagram znázorňující dotaz, který transformuje datový typ.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. Typ argumentu zdroje dat určuje typ proměnné rozsahu.  
  
2. Příkaz `select` vrátí `Name` vlastnost namísto `Customer` úplného objektu. Protože `Name` je řetězec, argument `custNameQuery` typu `string`je `Customer`, není .  
  
3. Protože `custNameQuery` je posloupnost řetězců, iterace `foreach` smyčky proměnné `string`musí být také .  
  
 Následující obrázek znázorňuje o něco složitější transformaci. Příkaz `select` vrátí anonymní typ, který zachycuje pouze `Customer` dva členy původního objektu.  
  
 ![Diagram znázorňující složitější dotaz, který transformuje datový typ.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. Argument typu zdroje dat je vždy typem proměnné rozsahu v dotazu.  
  
2. Vzhledem `select` k tomu, že příkaz vytváří anonymní typ, musí `var`být proměnná dotazu implicitně zadána pomocí .  
  
3. Vzhledem k tomu, že typ proměnné dotazu je implicitní, musí být implicitní také iterace proměnné ve `foreach` smyčce.  
  
## <a name="letting-the-compiler-infer-type-information"></a>Možnost, aby kompilátor odvodil informace o typu  
 I když byste měli pochopit vztahy typu v operaci dotazu, máte možnost nechat kompilátor uděláte veškerou práci za vás. Klíčové slovo [var](../../../language-reference/keywords/var.md) lze použít pro libovolnou místní proměnnou v operaci dotazu. Následující obrázek je podobný příkladčíslo 2, který byl popsán dříve. Kompilátor však poskytuje silný typ pro každou proměnnou v operaci dotazu.  
  
 ![Diagram, který zobrazuje tok typu s implicitním psaním.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 Další informace `var`o [souborech naleznete v tématu Implicitně zadané místní proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).  
