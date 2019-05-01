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
ms.openlocfilehash: 3b8ae80ff17ea2cf12c3d78c092dd3233ac0751d
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "63774015"
---
# <a name="type-relationships-in-linq-query-operations-c"></a>Vztahy typů v operacích dotazu LINQ (C#)
Chcete-li psát dotazy efektivně, je třeba porozumět, jak typy proměnných v dokončeném dotazu operace všechny vzájemně souvisí. Když pochopíte tyto vztahy se snadněji pochopit [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ukázky a příklady kódu v dokumentaci. Kromě toho budete rozumět co děje na pozadí, když jsou proměnné implicitně typované pomocí `var`.  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operace dotazu jsou silně typované ve zdroji dat, v samotném dotazu a ve spuštění dotazu. Typ proměnné dotazů musí být kompatibilní s typem prvků ve zdroji dat a typem iterační proměnné v `foreach` příkazu. Tvorba silných typů zaručuje, že jsou zachyceny chyby typu v době kompilace, kdy je lze opravit dříve, než se dotknou uživatelů.  
  
 Pro ukázání těchto vztahů typů většina příkladů, které následují, používá explicitní zadání pro všechny proměnné. Poslední příklad ukazuje, jak stejné zásady platí i při použití implicitního zápisu pomocí [var](../../../../csharp/language-reference/keywords/var.md).  
  
## <a name="queries-that-do-not-transform-the-source-data"></a>Dotazy, které Netransformují zdrojová Data  
 Následující ilustrace ukazuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] na objekty dotazování operace, která neslouží k transformaci na data. Zdroj obsahuje posloupnosti řetězců a výstup dotazu je také posloupnost řetězců.  
  
 ![Diagram znázorňující vztah datových typů v dotazu LINQ.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. Argument typu zdroje dat určuje typ rozsahu proměnných.  
  
2. Určuje typ objektu, který je vybraný typ proměnné dotazu. Tady `name` je řetězec. Proto, že je proměnná dotazu `IEnumerable<string>`.  
  
3. Proměnná dotazu je procházena `foreach` příkazu. Vzhledem k tomu, že je proměnná dotazu sekvencí řetězců, iterační proměnná je také řetězec.  
  
## <a name="queries-that-transform-the-source-data"></a>Dotazy, které transformují zdrojová Data  
 Následující ilustrace ukazuje [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] dotazové operace, který provádí jednoduché transformaci na data. Dotaz přebírá řadu `Customer` objektů jako vstup a vybere pouze `Name` vlastnosti ve výsledku. Protože `Name` je řetězec, dotaz vyprodukuje sekvenci řetězců jako výstup.  
  
 ![Diagram znázorňující, který transformuje datový typ dotazu.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. Argument typu zdroje dat určuje typ rozsahu proměnných.  
  
2. `select` Příkaz vrátí `Name` vlastnosti namísto kompletního `Customer` objektu. Protože `Name` je řetězec argument typu `custNameQuery` je `string`, nikoli `Customer`.  
  
3. Protože `custNameQuery` je posloupnost řetězců `foreach` iterační proměnná smyčky musí být také `string`.  
  
 Následující obrázek znázorňuje poněkud složitější transformaci. `select` Příkaz vrátí anonymní typ, který zachycuje pouze dva členy původního `Customer` objektu.  
  
 ![Diagram znázorňující komplexnější dotaz, který transformuje datový typ.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. Argument typu zdroje dat je vždy typ rozsahu proměnných v dotazu.  
  
2. Vzhledem k tomu, `select` příkaz produkuje anonymní typ, proměnná dotazu musí být implicitně typována pomocí `var`.  
  
3. Protože je typ proměnné dotazu implicitní, iterační proměnná ve `foreach` smyčky musí být také implicitní.  
  
## <a name="letting-the-compiler-infer-type-information"></a>Umožnit kompilátoru odvodit informace o typu  
 Přestože byste měli rozumět vztahům typů v operaci dotazu, máte možnost nechat kompilátor, aby udělal všechnu práci za vás. Klíčové slovo [var](../../../../csharp/language-reference/keywords/var.md) lze použít pro všechny místní proměnné v rámci operace dotazu. Na následujícím obrázku je podobně jako u příkladu 2, který byl popsán výše. Kompilátor však dodává silný typ pro každou proměnnou v operaci dotazu.  
  
 ![Diagram znázorňující tok typ s implicitního zápisu.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 Další informace o `var`, naleznete v tématu [implicitně typované lokální proměnné](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Viz také:

- [Začínáme s dotazy LINQ v jazyce C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
