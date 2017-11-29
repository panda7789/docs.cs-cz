---
title: "Návod: Zápis dotazů v C# (LINQ)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: get-started-article
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c0885c3cc989260cf67608bec0ff512c9f4835f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-writing-queries-in-c-linq"></a>Návod: Zápis dotazů v C# (LINQ)
Tento návod ukazuje funkce jazyka C#, které se používají k zápisu LINQ – výrazy dotazů.  
  
## <a name="create-a-c-project"></a>Vytvoření projektu v jazyce C#  
  
> [!NOTE]
>  Následující pokyny jsou pro sadu Visual Studio. Pokud používáte jiné vývojové prostředí, vytvořte projekt konzolové s odkazem na System.Core.dll a `using` direktivy pro <xref:System.Linq?displayProperty=nameWithType> oboru názvů.  
  
#### <a name="to-create-a-project-in-visual-studio"></a>Vytvoření projektu v sadě Visual Studio  
  
1.  Spuštění sady Visual Studio.  
  
2.  Na řádku nabídek zvolte **soubor**, **nový**, **projektu**.  
  
     **Nový projekt** otevře se dialogové okno.  
  
3.  Rozbalte položku **nainstalovaná**, rozbalte položku **šablony**, rozbalte položku **Visual C#**a potom zvolte **konzolové aplikace**.  
  
4.  V **název** textového pole zadejte jiný název nebo přijměte výchozí název a potom zvolte **OK** tlačítko.  
  
     Nový projekt se zobrazí v **Průzkumníku řešení**.  
  
5.  Všimněte si, že váš projekt odkazuje na System.Core.dll a `using` direktivy pro <xref:System.Linq?displayProperty=nameWithType> oboru názvů.  
  
## <a name="create-an-in-memory-data-source"></a>Vytvoření zdroje dat v paměti  
 Zdroj dat pro dotazy je jednoduchý seznam `Student` objekty. Každý `Student` záznam obsahuje křestní jméno, příjmení a pole celých čísel, které představuje jejich výsledků testu v třídě. Zkopírujte tento kód do projektu. Vezměte na vědomí následující vlastnosti:  
  
-   `Student` Třídy se skládá z automaticky implementované vlastnosti.  
  
-   Každý student v seznamu se inicializuje inicializátoru objektu.  
  
-   Samotný seznam se inicializuje pomocí inicializátoru kolekce.  
  
 Celou datovou strukturu bude inicializovat a vytvoření instance bez explicitního volání k žádnému konstruktor nebo explicitního člena přístup. Další informace o těchto nových funkcích najdete v tématu [Auto-Implemented vlastnosti](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) a [inicializátory objektu a kolekce](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
#### <a name="to-add-the-data-source"></a>Přidání zdroje dat  
  
-   Přidat `Student` třídy a inicializovaného seznam studentů `Program` třídy ve vašem projektu.  
  
     [!code-csharp[CsLinqGettingStarted#11](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_1.cs)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Přidání nového objektu Student do seznamu Students  
  
1.  Přidejte nový `Student` k `Students` seznamu, použijte název a testování skóre podle svého výběru. Zkuste zadat všechny nové informace studenty, aby bylo možné lépe další syntaxe pro inicializátoru objektu.  
  
## <a name="create-the-query"></a>Vytvoření dotazu  
  
#### <a name="to-create-a-simple-query"></a>Vytvoření jednoduchého dotazu  
  
-   Do aplikace `Main` metody vytvoření jednoduchého dotazu, který při spuštění, vygeneruje seznam všech studentů, jejichž skóre na první test byl větší než 90. Všimněte si, že protože celek `Student` je objekt vybrán, je typ dotazu `IEnumerable<Student>`. Kód použít taky implicitní zadáte pomocí [var](../../../../csharp/language-reference/keywords/var.md) – klíčové slovo, explicitní zadáním se používá ke jasně znázornění výsledků. (Další informace o `var`, najdete v části [implicitně typované lokální proměnné](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).)  
  
     Poznámka: dotaz na proměnnou rozsahu `student`, slouží jako odkaz na každý `Student` ve zdroji, poskytuje přístup ke členu pro každý objekt.  
  
 [!code-csharp[CsLINQGettingStarted#12](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_2.cs)]  
  
## <a name="execute-the-query"></a>Provedení dotazu  
  
#### <a name="to-execute-the-query"></a>Provedení dotazu  
  
1.  Nyní zápisu `foreach` smyčky, která způsobí, že dotaz provést. Vezměte na vědomí následující skutečnosti související kód:  
  
    -   Každý prvek v pořadí vrácených přistupuje prostřednictvím proměnné iterace ve `foreach` smyčky.  
  
    -   Typ této proměnné je `Student`, a typ proměnné v dotazu je kompatibilní, `IEnumerable<Student>`.  
  
2.  Po přidání tohoto kódu sestavení a spuštění aplikace a zobrazte výsledky v **konzoly** okno.  
  
 [!code-csharp[CsLINQGettingStarted#13](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_3.cs)]  
  
#### <a name="to-add-another-filter-condition"></a>Přidání další podmínky filtru  
  
1.  Můžete kombinovat více Boolean podmínek v `where` klauzule za účelem další upřesnění dotazu. Následující kód přidá podmínku tak, že dotaz vrátí ty studenty, jejichž první skóre bylo víc než 90 a jejichž poslední skóre nižší než 80. `where` Klauzule by měla vypadat přibližně následující kód.  
  
    ```  
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     Další informace najdete v tématu [kde klauzule](../../../../csharp/language-reference/keywords/where-clause.md).  
  
## <a name="modify-the-query"></a>Úprava dotazu  
  
#### <a name="to-order-the-results"></a>Řazení výsledků  
  
1.  Bude snazší výsledky kontroly, pokud jsou v nějakém pořadí. Můžete uspořádat vrácený pořadí pomocí libovolné dostupné pole ve zdrojové elementy. Například následující `orderby` klauzule řadí výsledky v abecedním pořadí od A do Z podle poslední název každé student. Přidejte následující `orderby` klauzule do dotazu, hned po `where` prohlášení a před `select` příkaz:  
  
    ```  
    orderby student.Last ascending  
    ```  
  
2.  Nyní změnit `orderby` klauzule, které se v obráceném pořadí řadí výsledky podle skóre na první testu z nejvyšší skóre skóre.  
  
    ```  
    orderby student.Scores[0] descending  
    ```  
  
3.  Změna `WriteLine` řetězec formátu, takže uvidíte skóre:  
  
    ```  
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     Další informace najdete v tématu [klauzule orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).  
  
#### <a name="to-group-the-results"></a>Seskupení výsledků  
  
1.  Seskupení je účinné ve výrazech dotazů. Dotaz s klauzuli group vytváří pořadí skupin a obsahuje každou skupinu jako celek `Key` a sekvenci, která se skládá ze všech členů této skupiny. Následující dotaz nové skupiny studenty pomocí první písmeno jeho příjmení jako klíč.  
  
     [!code-csharp[CsLINQGettingStarted#14](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_4.cs)]  
  
2.  Všimněte si, že typ dotazu se změnilo. Nyní vyvolá posloupnost skupiny, které mají `char` typ jako klíč a posloupnost `Student` objekty. Protože se změnil typ dotazu, následující kód změny `foreach` provádění cykly také:  
  
     [!code-csharp[CsLINQGettingStarted#15](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_5.cs)]  
  
3.  Spusťte aplikaci a zobrazit výsledky v **konzoly** okno.  
  
     Další informace najdete v tématu [group – klauzule](../../../../csharp/language-reference/keywords/group-clause.md).  
  
#### <a name="to-make-the-variables-implicitly-typed"></a>Převedení proměnných na implicitně typované proměnné  
  
1.  Explicitně kódování `IEnumerables` z `IGroupings` může být zdlouhavé. Můžete napsat stejný dotaz a `foreach` cykly mnohem snadněji pomocí `var`. `var` – Klíčové slovo nezmění typy objektů vašeho; je právě dává pokyn kompilátoru odvodit typy. Změnit typ `studentQuery` a proměnné iterace `group` k `var` a spusťte dotaz znovu. Všimněte si, že v vnitřní `foreach` smyčky, proměnné iterace je stále zadán jako `Student`, a dotaz funguje stejně jako předtím. Změna `s` proměnné iterace k `var` a spusťte dotaz znovu. Uvidíte, že dostanete přesně stejné výsledky.  
  
     [!code-csharp[CsLINQGettingStarted#16](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_6.cs)]  
  
     Další informace o [var](../../../../csharp/language-reference/keywords/var.md), najdete v části [implicitně typované lokální proměnné](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
#### <a name="to-order-the-groups-by-their-key-value"></a>Seřazení skupin podle hodnoty jejich klíče  
  
1.  Při spuštění předchozího dotazu, si všimnete, že skupiny nejsou v abecedním pořadí. Chcete-li toto nastavení změnit, je nutné zadat `orderby` klauzule po `group` klauzule. Ale pro použití `orderby` klauzule, musíte nejprve identifikátor, který slouží jako odkaz na skupiny vytvořené `group` klauzule. Zadejte identifikátor pomocí `into` – klíčové slovo, následujícím způsobem:  
  
     [!code-csharp[csLINQGettingStarted#17](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_7.cs)]  
  
     Při spuštění tohoto dotazu, zobrazí se, že skupiny jsou nyní seřazené podle abecedy.  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a>Zavedení identifikátoru s použitím klíčového slova let  
  
1.  Můžete použít `let` – klíčové slovo zavádět identifikátor pro žádný výsledek výraz ve výrazu dotazu. Tento identifikátor může být pro vaše pohodlí, jako v následujícím příkladu, nebo ji můžete zvýšit výkon uložením výsledky výrazu tak, aby nemá vypočítávat vícekrát.  
  
     [!code-csharp[csLINQGettingStarted#18](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_8.cs)]  
  
     Další informace najdete v tématu [let – klauzule](../../../../csharp/language-reference/keywords/let-clause.md).  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a>Použití syntaxe využívající metody ve výrazu dotazu  
  
1.  Jak je popsáno v [syntaxe dotazů a syntaxe využívající metody v technologii LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), některé operace dotazů lze vyjádřit pouze pomocí syntaxe využívající metody. Následující kód vypočítá celkové skóre pro každou `Student` zdrojové sekvence a potom volání `Average()` metodu na výsledky tohoto dotazu pro výpočet průměrné skóre třídy. Poznamenejte si umístění v závorkách výrazu dotazu.  
  
     [!code-csharp[csLINQGettingStarted#19](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_9.cs)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a>Transformace nebo projekce v klauzuli select  
  
1.  Je velmi běžné pro dotaz k vytvoření pořadí, jehož elementy liší z elementů ve zdrojovém pořadí. Odstranit nebo komentář předchozího dotazu a provádění smyčky a nahraďte ji následujícím kódem. Všimněte si, že dotaz vrátí posloupnosti řetězců (ne `Students`), a tento fakt se odrazí v `foreach` smyčky.  
  
     [!code-csharp[csLINQGettingStarted#20](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_10.cs)]  
  
2.  Kód dříve v tomto návodu ukázalo, že průměrná třída skóre je přibližně 334. K vytvoření posloupnost `Students` jejichž celkové skóre je větší než třída průměr, společně s jejich `Student ID`, můžete použít anonymní typ v `select` příkaz:  
  
     [!code-csharp[csLINQGettingStarted#21](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_11.cs)]  
  
## <a name="next-steps"></a>Další kroky  
 Jakmile se seznámíte s základní aspektů práce s dotazy v jazyce C#, jste připravení číst dokumentace a ukázky pro konkrétní typ LINQ zprostředkovatele, které vás zajímají:  
  
 [Technologie LINQ to SQL](https://msdn.microsoft.com/library/bb386976)  
  
 [LINQ na DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [Technologie LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [LINQ na objekty (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>Viz také  
 [Language-Integrated Query (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)  
 [Začínáme s dotazy LINQ v jazyku C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [LINQ – výrazy dotazů](../../../../csharp/programming-guide/linq-query-expressions/index.md)
