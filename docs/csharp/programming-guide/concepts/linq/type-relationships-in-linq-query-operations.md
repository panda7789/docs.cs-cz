---
title: Vztahy typů v operacích dotazu LINQ (C#)
description: Přečtěte si, jak typy proměnných v dotazu LINQ vzájemně souvisí. Operace dotazů LINQ jsou silně typované ve zdroji dat, v dotazu a v provádění.
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
ms.openlocfilehash: 20f0b37a156e3b3f9c63f14cb83d678d26f685ee
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302279"
---
# <a name="type-relationships-in-linq-query-operations-c"></a>Vztahy typů v operacích dotazu LINQ (C#)
Chcete-li efektivně zapisovat dotazy, měli byste pochopit, jak typy proměnných v úplné operaci dotazu vzájemně souvisí. Pokud rozumíte těmto vztahům, budete snadněji pochopit ukázky LINQ a příklady kódu v dokumentaci. Kromě toho můžete pochopit, co se stane na pozadí, pokud jsou proměnné implicitně typované pomocí `var` .  
  
 Operace dotazů LINQ jsou silně typované ve zdroji dat, v samotném dotazu a v provádění dotazu. Typ proměnných v dotazu musí být kompatibilní s typem prvků ve zdroji dat a typem proměnné iterace v `foreach` příkazu. Toto silné zadání zaručuje, že při kompilaci jsou zachyceny chyby typu, pokud je lze opravit předtím, než se uživatelé dostanou.  
  
 Aby bylo možné předvést tyto vztahy typů, většina příkladů, které následují, používá explicitní psaní pro všechny proměnné. Poslední příklad ukazuje, jak se stejné zásady použijí, i když použijete implicitní zadání pomocí [var](../../../language-reference/keywords/var.md).  
  
## <a name="queries-that-do-not-transform-the-source-data"></a>Dotazy, které netransformují zdrojová data  
 Následující ilustrace znázorňuje LINQ to Objects operaci dotazování, která neprovede žádné transformace dat. Zdroj obsahuje posloupnost řetězců a výstup dotazu je také posloupnost řetězců.  
  
 ![Diagram, který zobrazuje vztah datových typů v dotazu LINQ.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. Argument typu zdroje dat určuje typ proměnné rozsahu.  
  
2. Typ objektu, který je vybrán, určuje typ proměnné dotazu. Zde `name` je řetězec. Proto proměnná dotazu je `IEnumerable<string>` .  
  
3. Proměnná dotazu se opakuje v `foreach` příkazu. Vzhledem k tomu, že je proměnná dotazu posloupností řetězců, je proměnná iterace také řetězcem.  
  
## <a name="queries-that-transform-the-source-data"></a>Dotazy, které transformují zdrojová data  
 Následující ilustrace znázorňuje [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operaci dotazu, která provádí jednoduchou transformaci dat. Dotaz provede jako vstup sekvenci `Customer` objektů a `Name` ve výsledku vybere pouze vlastnost. Vzhledem k tomu `Name` , že je řetězec, dotaz vytváří sekvenci řetězců jako výstup.  
  
 ![Diagram znázorňující dotaz, který transformuje datový typ.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. Argument typu zdroje dat určuje typ proměnné rozsahu.  
  
2. `select`Příkaz vrátí `Name` vlastnost namísto celého `Customer` objektu. Protože `Name` je řetězec, argument typu `custNameQuery` je `string` , not `Customer` .  
  
3. Vzhledem k tomu `custNameQuery` , že je sekvence řetězců, `foreach` iterační proměnná smyčky musí být také `string` .  
  
 Následující ilustrace znázorňuje mírně složitější transformaci. `select`Příkaz vrátí anonymní typ, který zachycuje pouze dva členy původního `Customer` objektu.  
  
 ![Diagram znázorňující složitější dotaz, který transformuje datový typ.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. Argument typu zdroje dat je vždy typ proměnné rozsahu v dotazu.  
  
2. Vzhledem k tomu `select` , že příkaz vytvoří anonymní typ, proměnná dotazu musí být implicitně zadána pomocí `var` .  
  
3. Vzhledem k tomu, že typ proměnné dotazu je implicitní, musí být proměnná iterace ve `foreach` smyčce také implicitní.  
  
## <a name="letting-the-compiler-infer-type-information"></a>Umožnění odvození informací o typu kompilátoru  
 I když byste měli pochopit vztahy typů v operaci dotazu, máte možnost nechat kompilátor provádět veškerou práci za vás. Klíčové slovo [var](../../../language-reference/keywords/var.md) lze použít pro libovolnou místní proměnnou v operaci dotazu. Následující obrázek je podobný ukázkovému číslu 2, které bylo popsáno dříve. Nicméně kompilátor poskytuje silný typ pro každou proměnnou v operaci dotazu.  
  
 ![Diagram, který zobrazuje tok typu s implicitním zadáním.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 Další informace o naleznete `var` v tématu [implicitně typované lokální proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).  
