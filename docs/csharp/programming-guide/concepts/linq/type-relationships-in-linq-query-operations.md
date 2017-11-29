---
title: "Vztahy typů v operacích dotazu LINQ (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
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
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a088a7f673a9f6aea7a0f50e18746259171bb7e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="type-relationships-in-linq-query-operations-c"></a>Vztahy typů v operacích dotazu LINQ (C#)
Zápis dotazů efektivně, byste měli porozumět, jak typy proměnných v rámci dokončení dotazu operace všechny vztahují k sobě navzájem. Pokud budete rozumět tomu tyto vztahy se snadněji pochopit [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ukázky a příklady kódu v dokumentaci. Kromě toho bude pochopit, co se děje na pozadí při proměnné jsou implicitně typované pomocí `var`.  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]operace dotazů jsou silného typu ve zdroji dat, v samotném dotazu a při provádění dotazu. Typ proměnné v dotazu musí být kompatibilní s typem elementů ve zdroji dat a s typem proměnné iterace ve `foreach` příkaz. Tento silného typování zaručuje, že typ chyby jsou zachyceny v době kompilace při jejich lze opravit, než uživatelům stane je.  
  
 K prokázání tyto relace typu, většina příkladů, které následují použijte explicitní zadáte pro všechny proměnné. Poslední příklad ukazuje, jak stejné zásady platí, i když použijete implicitní zadáte pomocí [var](../../../../csharp/language-reference/keywords/var.md).  
  
## <a name="queries-that-do-not-transform-the-source-data"></a>Dotazy, které nebudou transformovat zdrojová Data  
 Následující obrázek znázorňuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] na objekty dotazu operace, která provádí data žádná transformace. Zdroj obsahuje posloupnost řetězce a výstupu dotazu je také pořadí řetězce.  
  
 ![Typy vztah dat v dotazu LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_flow1.png "LINQ_flow1")  
  
1.  Argument typu zdroje dat určuje typ proměnné rozsahu.  
  
2.  Typ objektu, který je vybraný Určuje typ proměnné v dotazu. Zde `name` je řetězec. Proměnné dotazu je proto `IEnumerable` \<řetězec >.  
  
3.  Proměnné dotazu je vstupní přes `foreach` příkaz. Proměnné dotazu je posloupnost řetězce, a proto je řetězec také proměnné iterace.  
  
## <a name="queries-that-transform-the-source-data"></a>Dotazy, které transformace zdrojová Data  
 Následující obrázek znázorňuje [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operace, která provádí jednoduché transformaci dat dotazů. Dotaz trvá posloupnost `Customer` objekty jako vstup a vybere pouze `Name` vlastnost ve výsledku. Protože `Name` je řetězec dotazu vytváří a pořadí řetězce jako výstup.  
  
 ![Dotaz, který transformuje datový typ](../../../../csharp/programming-guide/concepts/linq/media/linq_flow2.png "LINQ_flow2")  
  
1.  Argument typu zdroje dat určuje typ proměnné rozsahu.  
  
2.  `select` Příkaz vrátí `Name` vlastnost místo kompletní `Customer` objektu. Protože `Name` je řetězec, typ argument `custNameQuery` je `string`, nikoli `Customer`.  
  
3.  Protože `custNameQuery` je posloupnost řetězce, `foreach` musí být také proměnné iterace smyčky `string`.  
  
 Následující obrázek znázorňuje trochu složitější transformace. `select` Příkaz vrací anonymní typ, který zachycuje právě dva členy původního `Customer` objektu.  
  
 ![Dotaz, který transformuje datový typ](../../../../csharp/programming-guide/concepts/linq/media/linq_flow3.png "LINQ_flow3")  
  
1.  Argument typu zdroje dat je vždy typ proměnné rozsahu v dotazu.  
  
2.  Protože `select` příkaz vytvořil anonymní typ, proměnné dotazu musí být implicitně typované pomocí `var`.  
  
3.  Typ proměnné v dotazu je implicitní, proměnné iterace ve `foreach` smyčky, musí být také implicitní.  
  
## <a name="letting-the-compiler-infer-type-information"></a>Upozornění kompilátoru odvození informací o typu  
 I když byste měli porozumět vztahy typů v operaci dotazu, máte možnost povolit, aby kompilátoru to pro vás všechnu práci. Klíčové slovo [var](../../../../csharp/language-reference/keywords/var.md) lze použít pro všechny místní proměnné v operaci dotazu. Na následujícím obrázku je podobný příklad číslem 2, který byl dříve popsané. Kompilátor však poskytuje silného typu pro každou proměnnou v operaci dotazu.  
  
 ![Zadejte toku s implicitní zadáním](../../../../csharp/programming-guide/concepts/linq/media/linq_flow4.png "LINQ_flow4")  
  
 Další informace o `var`, najdete v části [implicitně typované lokální proměnné](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Viz také  
 [Začínáme s dotazy LINQ v jazyku C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
