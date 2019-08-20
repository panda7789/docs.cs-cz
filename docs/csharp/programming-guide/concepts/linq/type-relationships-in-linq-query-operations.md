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
ms.openlocfilehash: 42519a74be1bd6934bc7a3304d154321697d128c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591017"
---
# <a name="type-relationships-in-linq-query-operations-c"></a>Vztahy typů v operacích dotazu LINQ (C#)
Chcete-li efektivně zapisovat dotazy, měli byste pochopit, jak typy proměnných v úplné operaci dotazu vzájemně souvisí. Pokud rozumíte těmto vztahům, budete snadněji pochopit [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ukázky a příklady kódu v dokumentaci. Kromě toho můžete pochopit, co se stane na pozadí, pokud jsou proměnné implicitně typované pomocí `var`.  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]operace dotazů jsou silně typované ve zdroji dat, v samotném dotazu a v provádění dotazu. Typ proměnných v dotazu musí být kompatibilní s typem prvků ve zdroji dat a typem proměnné iterace v `foreach` příkazu. Toto silné zadání zaručuje, že při kompilaci jsou zachyceny chyby typu, pokud je lze opravit předtím, než se uživatelé dostanou.  
  
 Aby bylo možné předvést tyto vztahy typů, většina příkladů, které následují, používá explicitní psaní pro všechny proměnné. Poslední příklad ukazuje, jak se stejné zásady použijí, i když použijete implicitní zadání pomocí [var](../../../language-reference/keywords/var.md).  
  
## <a name="queries-that-do-not-transform-the-source-data"></a>Dotazy, které netransformují zdrojová data  
 Následující ilustrace znázorňuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operaci dotazování na objekty, která neprovede žádné transformace dat. Zdroj obsahuje posloupnost řetězců a výstup dotazu je také posloupnost řetězců.  
  
 ![Diagram, který zobrazuje vztah datových typů v dotazu LINQ.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. Argument typu zdroje dat určuje typ proměnné rozsahu.  
  
2. Typ objektu, který je vybrán, určuje typ proměnné dotazu. Zde `name` je řetězec. Proto proměnná dotazu je `IEnumerable<string>`.  
  
3. Proměnná dotazu se opakuje v `foreach` příkazu. Vzhledem k tomu, že je proměnná dotazu posloupností řetězců, je proměnná iterace také řetězcem.  
  
## <a name="queries-that-transform-the-source-data"></a>Dotazy, které transformují zdrojová data  
 Následující ilustrace znázorňuje [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operaci dotazu, která provádí jednoduchou transformaci dat. Dotaz provede jako vstup sekvenci `Customer` objektů a ve výsledku vybere `Name` pouze vlastnost. Vzhledem `Name` k tomu, že je řetězec, dotaz vytváří sekvenci řetězců jako výstup.  
  
 ![Diagram znázorňující dotaz, který transformuje datový typ.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. Argument typu zdroje dat určuje typ proměnné rozsahu.  
  
2. Příkaz vrátí vlastnost namísto celého `Customer`objektu. `Name` `select` Protože `Name` je řetězec, `custNameQuery` argument typu je `string`, not `Customer`.  
  
3. Vzhledem `custNameQuery` k tomu `foreach` , že je sekvence řetězců, iterační `string`proměnná smyčky musí být také.  
  
 Následující ilustrace znázorňuje mírně složitější transformaci. Příkaz vrátí anonymní typ, který zachycuje pouze dva členy původního `Customer` objektu. `select`  
  
 ![Diagram znázorňující složitější dotaz, který transformuje datový typ.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. Argument typu zdroje dat je vždy typ proměnné rozsahu v dotazu.  
  
2. Vzhledem k tomu, že `var` příkazvytvoříanonymnítyp,proměnnádotazumusíbýtimplicitnězadánapomocí.`select`  
  
3. Vzhledem k tomu, že typ proměnné dotazu je implicitní, musí být proměnná iterace ve `foreach` smyčce také implicitní.  
  
## <a name="letting-the-compiler-infer-type-information"></a>Umožnění odvození informací o typu kompilátoru  
 I když byste měli pochopit vztahy typů v operaci dotazu, máte možnost nechat kompilátor provádět veškerou práci za vás. Klíčové slovo [var](../../../language-reference/keywords/var.md) lze použít pro libovolnou místní proměnnou v operaci dotazu. Následující obrázek je podobný ukázkovému číslu 2, které bylo popsáno dříve. Nicméně kompilátor poskytuje silný typ pro každou proměnnou v operaci dotazu.  
  
 ![Diagram, který zobrazuje tok typu s implicitním zadáním.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 Další informace o `var`naleznete v tématu [implicitně typované lokální proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).  
