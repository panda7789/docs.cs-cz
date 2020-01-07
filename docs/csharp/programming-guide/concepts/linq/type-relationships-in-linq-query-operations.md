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
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635610"
---
# <a name="type-relationships-in-linq-query-operations-c"></a>Vztahy typů v operacích dotazu LINQ (C#)
Chcete-li efektivně zapisovat dotazy, měli byste pochopit, jak typy proměnných v úplné operaci dotazu vzájemně souvisí. Pokud rozumíte těmto vztahům, budete snadněji pochopit ukázky LINQ a příklady kódu v dokumentaci. Kromě toho budete rozumět tomu, co se děje na pozadí, když jsou proměnné implicitně typové pomocí `var`.  
  
 Operace dotazů LINQ jsou silně typované ve zdroji dat, v samotném dotazu a v provádění dotazu. Typ proměnných v dotazu musí být kompatibilní s typem prvků ve zdroji dat a typem proměnné iterace v příkazu `foreach`. Toto silné zadání zaručuje, že při kompilaci jsou zachyceny chyby typu, pokud je lze opravit předtím, než se uživatelé dostanou.  
  
 Aby bylo možné předvést tyto vztahy typů, většina příkladů, které následují, používá explicitní psaní pro všechny proměnné. Poslední příklad ukazuje, jak se stejné zásady použijí, i když použijete implicitní zadání pomocí [var](../../../language-reference/keywords/var.md).  
  
## <a name="queries-that-do-not-transform-the-source-data"></a>Dotazy, které netransformují zdrojová data  
 Následující ilustrace znázorňuje LINQ to Objects operaci dotazování, která neprovede žádné transformace dat. Zdroj obsahuje posloupnost řetězců a výstup dotazu je také posloupnost řetězců.  
  
 ![Diagram, který zobrazuje vztah datových typů v dotazu LINQ.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. Argument typu zdroje dat určuje typ proměnné rozsahu.  
  
2. Typ objektu, který je vybrán, určuje typ proměnné dotazu. Zde `name` je řetězec. Proto je proměnná dotazu `IEnumerable<string>`.  
  
3. Proměnná dotazu je iterovaná v příkazu `foreach`. Vzhledem k tomu, že je proměnná dotazu posloupností řetězců, je proměnná iterace také řetězcem.  
  
## <a name="queries-that-transform-the-source-data"></a>Dotazy, které transformují zdrojová data  
 Následující ilustrace znázorňuje [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operaci dotazování, která provádí jednoduchou transformaci dat. Dotaz přebírá sekvenci `Customer` objektů jako vstup a ve výsledku vybere pouze vlastnost `Name`. Vzhledem k tomu, že `Name` je řetězec, dotaz vytvoří sekvenci řetězců jako výstup.  
  
 ![Diagram znázorňující dotaz, který transformuje datový typ.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. Argument typu zdroje dat určuje typ proměnné rozsahu.  
  
2. Příkaz `select` vrátí vlastnost `Name` namísto celého objektu `Customer`. Vzhledem k tomu, že `Name` je řetězec, argument typu `custNameQuery` je `string`, nikoli `Customer`.  
  
3. Vzhledem k tomu, že `custNameQuery` je sekvence řetězců, iterační proměnná `foreach` smyčky musí být také `string`.  
  
 Následující ilustrace znázorňuje mírně složitější transformaci. Příkaz `select` vrací anonymní typ, který zachycuje pouze dva členy původního objektu `Customer`.  
  
 ![Diagram znázorňující složitější dotaz, který transformuje datový typ.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. Argument typu zdroje dat je vždy typ proměnné rozsahu v dotazu.  
  
2. Vzhledem k tomu, že příkaz `select` vytváří anonymní typ, musí být proměnná dotazu implicitně zapsána pomocí `var`.  
  
3. Vzhledem k tomu, že typ proměnné dotazu je implicitní, musí být proměnná iterace ve smyčce `foreach` také implicitní.  
  
## <a name="letting-the-compiler-infer-type-information"></a>Umožnění odvození informací o typu kompilátoru  
 I když byste měli pochopit vztahy typů v operaci dotazu, máte možnost nechat kompilátor provádět veškerou práci za vás. Klíčové slovo [var](../../../language-reference/keywords/var.md) lze použít pro libovolnou místní proměnnou v operaci dotazu. Následující obrázek je podobný ukázkovému číslu 2, které bylo popsáno dříve. Nicméně kompilátor poskytuje silný typ pro každou proměnnou v operaci dotazu.  
  
 ![Diagram, který zobrazuje tok typu s implicitním zadáním.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 Další informace o `var`naleznete v tématu [implicitně typované lokální proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).  
